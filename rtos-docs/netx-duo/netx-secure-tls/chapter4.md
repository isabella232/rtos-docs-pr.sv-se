---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX Secure Services
description: Det här kapitlet innehåller en beskrivning av alla NetX säkra tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826949"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="a87cb-103">Kapitel 4 – Beskrivning av Azure återställnings tider NetX Secure Services</span><span class="sxs-lookup"><span data-stu-id="a87cb-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="a87cb-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-säkra tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="a87cb-105">I avsnittet "returnera värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_SECURE_DISABLE_ERROR_CHECKING** makro som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="a87cb-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="a87cb-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="a87cb-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="a87cb-107">Utför self_test på krypterings metoderna</span><span class="sxs-lookup"><span data-stu-id="a87cb-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="a87cb-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="a87cb-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="a87cb-109">Beräknar hash-värde med user_supplied hash-funktion</span><span class="sxs-lookup"><span data-stu-id="a87cb-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="a87cb-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="a87cb-111">Ange det aktiva identitets certifikatet för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="a87cb-113">Ange en Pre_Shared nyckel för en NetX Secure TLS-klientsession</span><span class="sxs-lookup"><span data-stu-id="a87cb-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="a87cb-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="a87cb-115">Initierar NetX Secure TLS-modulen]</span><span class="sxs-lookup"><span data-stu-id="a87cb-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="a87cb-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="a87cb-117">Lägg till ett lokalt certifikat till NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="a87cb-119">Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn</span><span class="sxs-lookup"><span data-stu-id="a87cb-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="a87cb-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="a87cb-121">Ta bort det lokala certifikatet från NetX Secure TLS-sessionen</span><span class="sxs-lookup"><span data-stu-id="a87cb-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="a87cb-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="a87cb-123">Beräkna storleken på kryptografiska metadata för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="a87cb-125">Allokera ett paket för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="a87cb-127">Lägga till en Pre_Shared nyckel till en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="a87cb-129">Allokera utrymme för certifikatet som tillhandahålls av en fjärran sluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="a87cb-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="a87cb-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="a87cb-131">Allokera utrymme för alla certifikat som tillhandahålls av en fjärran sluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="a87cb-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="a87cb-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="a87cb-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="a87cb-133">Ledigt utrymme allokerat för inkommande certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="a87cb-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="a87cb-135">Lägg till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="a87cb-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="a87cb-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="a87cb-137">Hitta ett certifikat med en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="a87cb-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="a87cb-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="a87cb-139">Ta bort ett lokalt Server certifikat med en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="a87cb-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="a87cb-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="a87cb-141">Konfigurera en motringning för TLS som ska användas för ytterligare certifikat validering</span><span class="sxs-lookup"><span data-stu-id="a87cb-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="a87cb-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="a87cb-143">Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-klient hand skakning</span><span class="sxs-lookup"><span data-stu-id="a87cb-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="a87cb-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="a87cb-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="a87cb-145">Aktivera client X. 509-verifiering och allokera utrymme för klient certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="a87cb-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="a87cb-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="a87cb-147">Inaktivera autentisering av klient certifikat för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="a87cb-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="a87cb-149">Aktivera autentisering av klient certifikat för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="a87cb-151">Skapa en NetX Secure TLS-session för säker kommunikation</span><span class="sxs-lookup"><span data-stu-id="a87cb-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="a87cb-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="a87cb-153">Ta bort en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="a87cb-155">Avsluta en aktiv NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="a87cb-157">Ställ in bufferten för paket ommontering för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="a87cb-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="a87cb-159">Åsidosätt standard versionen av TLS-protokollet för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="a87cb-161">Ta emot data från en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="a87cb-163">Tilldela ett återanrop som ska anropas i början av en omförhandling av en session</span><span class="sxs-lookup"><span data-stu-id="a87cb-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="a87cb-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="a87cb-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="a87cb-165">Starta en handhandlings hand skakning med fjärrvärden</span><span class="sxs-lookup"><span data-stu-id="a87cb-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="a87cb-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="a87cb-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="a87cb-167">Ta bort och Återställ en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="a87cb-169">Skicka data via en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="a87cb-171">Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-servers hand skakning</span><span class="sxs-lookup"><span data-stu-id="a87cb-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="a87cb-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="a87cb-173">Parsa ett Servernamnindikator-tillägg (SNI) som tagits emot från en TLS-klient</span><span class="sxs-lookup"><span data-stu-id="a87cb-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="a87cb-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="a87cb-175">Ange ett Servernamnindikator-tillägg (SNI) som ska skickas till en fjärrserver</span><span class="sxs-lookup"><span data-stu-id="a87cb-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="a87cb-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="a87cb-177">Starta en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="a87cb-179">Tilldela en timestamp-funktion till en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="a87cb-181">Lägg till betrott certifikat i NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="a87cb-183">Ta bort betrott certifikat från NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="a87cb-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="a87cb-185">Initiera X. 509-certifikat för NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="a87cb-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="a87cb-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="a87cb-187">Kontrol lera DNS-namn mot X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="a87cb-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="a87cb-189">Kontrol lera X. 509-certifikatet mot en angiven lista över återkallade certifikat (CRL)]</span><span class="sxs-lookup"><span data-stu-id="a87cb-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="a87cb-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="a87cb-191">Initiera en X. 509 DNS-namn struktur</span><span class="sxs-lookup"><span data-stu-id="a87cb-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="a87cb-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="a87cb-193">Hitta och parsa ett tillägg för utökad nyckel användning i X. 509 i ett X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="a87cb-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="a87cb-195">Hitta och returnera ett X. 509-tillägg i ett X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="a87cb-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="a87cb-197">Hitta och parsa ett tillägg för nyckel användning i X. 509 i ett X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="a87cb-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="a87cb-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="a87cb-199">Utför självtest på krypterings metoderna</span><span class="sxs-lookup"><span data-stu-id="a87cb-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-201">Description</span></span>

<span data-ttu-id="a87cb-202">Den här tjänsten körs via de självtester som används av krypterings metod för att verifiera.</span><span class="sxs-lookup"><span data-stu-id="a87cb-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="a87cb-203">Själv testet är bara tillgängligt om NetX-biblioteket har skapats med symbolen NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definierat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="a87cb-204">För varje krypterings metod som stöds tillhandahåller självtesten fördefinierade indata och verifierade utdata matchar det fördefinierade förväntade värdet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="a87cb-205">NetX för säker kryptering stöder följande algoritmer och nyckel storlekar:</span><span class="sxs-lookup"><span data-stu-id="a87cb-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="a87cb-206">DES: kryptering och dekryptering</span><span class="sxs-lookup"><span data-stu-id="a87cb-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="a87cb-207">Tredubbel DES (3DES): kryptering och dekryptering</span><span class="sxs-lookup"><span data-stu-id="a87cb-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="a87cb-208">AES: 128-, 192-, 256-bitars nyckel storlek, kryptering och dekryptering i CBC-läge och räknar läge.</span><span class="sxs-lookup"><span data-stu-id="a87cb-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="a87cb-209">HMAC-MD5: autentisering och hash-beräkning</span><span class="sxs-lookup"><span data-stu-id="a87cb-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="a87cb-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, autentisering och hash-beräkning</span><span class="sxs-lookup"><span data-stu-id="a87cb-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="a87cb-211">MD5: autentisering</span><span class="sxs-lookup"><span data-stu-id="a87cb-211">MD5: authentication</span></span>
- <span data-ttu-id="a87cb-212">Pseudo – slumpmässig funktion (PRF): PRF_HMAC_SHA1 och PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="a87cb-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="a87cb-213">RSA: 1024-, 2048-, 4096-bitars RSA-åtgärd för PowerPivot-modul</span><span class="sxs-lookup"><span data-stu-id="a87cb-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="a87cb-214">SHA: SHA1 (96-och 160-bitars), SHA2 (256bit, 384bit, 512bit)-autentisering</span><span class="sxs-lookup"><span data-stu-id="a87cb-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="a87cb-215">Den här funktionen har inbyggda vektorer för de krypteringsalgoritmer som anges ovan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="a87cb-216">Det testar dock bara de som anges i *cipher_table* som har skickats till den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="a87cb-217">För en TLS-session används till exempel endast ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, den här funktionen utför självtest på RSA (1024-, 2048-, 4096-bitars), AES-CBC (128-bit) och SHA1.</span><span class="sxs-lookup"><span data-stu-id="a87cb-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-218">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-218">Parameters</span></span>

- <span data-ttu-id="a87cb-219">**crypto_table** Pekare till tabellen för kryptografi som används av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="a87cb-220">Detta är samma crypto_table som skickas till **_nx_secure_tls_session_create ()-_** anropet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="a87cb-221">**metadata** Pekar på utrymme för området för kryptografiska metadata.</span><span class="sxs-lookup"><span data-stu-id="a87cb-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="a87cb-222">.</span><span class="sxs-lookup"><span data-stu-id="a87cb-222">.</span></span>
- <span data-ttu-id="a87cb-223">**metadata_size** Storlek på bufferten för metadata.</span><span class="sxs-lookup"><span data-stu-id="a87cb-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-224">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-224">Return Values</span></span>

- <span data-ttu-id="a87cb-225">**NX_SECURE_TLS_SUCCESS** (0X00) har testat de kryptografiska metoder som angetts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="a87cb-226">**NX_PTR_ERROR** (0X07) ogiltig struktur för kryptografisk metod</span><span class="sxs-lookup"><span data-stu-id="a87cb-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="a87cb-227">Det gick inte att kontrol lera **NX_NOT_SUCCESSFUL** (0x43).</span><span class="sxs-lookup"><span data-stu-id="a87cb-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-228">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-228">Allowed From</span></span>

<span data-ttu-id="a87cb-229">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a87cb-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-230">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-230">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-231">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-231">See Also</span></span>

- <span data-ttu-id="a87cb-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="a87cb-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="a87cb-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="a87cb-234">Beräknar hash-värde med hjälp av en användardefinierad hash-funktion</span><span class="sxs-lookup"><span data-stu-id="a87cb-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-235">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-236">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-236">Description</span></span>

<span data-ttu-id="a87cb-237">Den här funktionen beräknar hash-värdet för data strömmen i det angivna minnes området med hjälp av den angivna HMAC-kryptografi metoden och nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="a87cb-238">Compute-funktionen modul-hash är bara tillgänglig om NetX Secure Library skapas med följande symbol som definieras: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="a87cb-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-239">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-239">Parameters</span></span>

- <span data-ttu-id="a87cb-240">**hmac_ptr** Pekar på den HMAC-kryptografiska metod som används för beräkning av hash-värde.</span><span class="sxs-lookup"><span data-stu-id="a87cb-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="a87cb-241">**start_address** Start adressen för databufferten</span><span class="sxs-lookup"><span data-stu-id="a87cb-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="a87cb-242">**end_address** Den avslutande adressen för databufferten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="a87cb-243">Observera att hash-beräkningen inte omfattar data i den här end_address.</span><span class="sxs-lookup"><span data-stu-id="a87cb-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="a87cb-244">**nyckel** Den nyckel sträng som används i HMAC-beräkningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="a87cb-245">**key_length** Nyckel strängens storlek i byte</span><span class="sxs-lookup"><span data-stu-id="a87cb-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="a87cb-246">**metadata** Pekar på utrymmet som används av HMAC-algoritmen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="a87cb-247">**metadata_size** Storlek på bufferten för metadata.</span><span class="sxs-lookup"><span data-stu-id="a87cb-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="a87cb-248">**output_buffer** Minnes platsen där hash-utdata lagras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="a87cb-249">**output_buffer_size** Tillgängligt utrymme för utdatabufferten i byte</span><span class="sxs-lookup"><span data-stu-id="a87cb-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="a87cb-250">**actual_size** Returneras av funktionen som indikerar det faktiska antalet byte som skrivs till output_buffer.</span><span class="sxs-lookup"><span data-stu-id="a87cb-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-251">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-251">Return Values</span></span>

- <span data-ttu-id="a87cb-252">**0** beräknade hash-värdet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="a87cb-253">**1** det gick inte att beräkna hashen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-254">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-254">Allowed From</span></span>

<span data-ttu-id="a87cb-255">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a87cb-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-256">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-256">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-257">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-257">See Also</span></span>

- <span data-ttu-id="a87cb-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="a87cb-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="a87cb-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="a87cb-260">Ange det aktiva identitets certifikatet för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-261">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="a87cb-262">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-262">Description</span></span>

<span data-ttu-id="a87cb-263">Den här tjänsten är avsedd att anropas inifrån en motringning för session (se nx_secure_tls_session_client_callback_set och nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="a87cb-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="a87cb-264">När det anropas med en tidigare initierad NX_SECURE_X509_CERT-struktur, kommer certifikatet att användas i stället för standard identitets certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="a87cb-265">I de flesta fall måste certifikatet ha lagts till i det lokala arkivet (se nx_secure_tls_local_certificate_add) eller så kan TLS-handskakningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="a87cb-266">Den här tjänsten är avsedd att tillåta TLS att stödja flera identitets certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="a87cb-267">Detta är användbart för en TLS-server som hanterar flera nätverks adresser så att servern kan välja ett lämpligt certifikat för att tillhandahålla fjärrklienten beroende på klientens start punkt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="a87cb-268">För en TLS-klient kan den här rutinen användas för att ändra certifikatet som skickas till en fjärrserver vid körning när servern har identifierat sig själv i TLS-handskakningen (detta är mer sällsynt än TLS-serverns användnings fall).</span><span class="sxs-lookup"><span data-stu-id="a87cb-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="a87cb-269">Om flera certifikat kan dela samma X. 509-unika namn måste certifikaten läggas till med nx_secure_tls_server_certificate_add, vilket ger en numerisk identifierare separat från certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-270">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-270">Parameters</span></span>

- <span data-ttu-id="a87cb-271">**session_ptr** Pekare till en TLS-sessionsbiljett som överförts till återanropet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="a87cb-272">**certifikat** Pekar på ett initierat X. 509-certifikat som ska användas för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-273">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-273">Return Values</span></span>

- <span data-ttu-id="a87cb-274">**NX_SUCCESS** (0x00) har slutfört tilldelningen av certifikat till sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="a87cb-275">**NX_PTR_ERROR** (0X07) ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-276">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-276">Allowed From</span></span>

<span data-ttu-id="a87cb-277">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-278">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-278">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-279">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-279">See Also</span></span>

- <span data-ttu-id="a87cb-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="a87cb-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="a87cb-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="a87cb-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="a87cb-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="a87cb-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="a87cb-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="a87cb-288">Ange en i förväg delad nyckel för en NetX Secure TLS-klientsession</span><span class="sxs-lookup"><span data-stu-id="a87cb-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-289">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="a87cb-290">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-290">Description</span></span>

<span data-ttu-id="a87cb-291">Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett kontroll block för TLS-session och anger att PSK ska användas i efterföljande TLS-klientanslutningar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="a87cb-292">PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.</span><span class="sxs-lookup"><span data-stu-id="a87cb-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="a87cb-293">I det här fallet är PSK associerat med en speciell fjärran sluten TLS-server som TLS-klienten vill kommunicera med.</span><span class="sxs-lookup"><span data-stu-id="a87cb-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="a87cb-294">Det PSK-värde som anges via denna API kommer att tillhandahållas till värden för fjärr-TLS-servern under nästa TLS-handskakning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-295">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-295">Parameters</span></span>

- <span data-ttu-id="a87cb-296">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-297">**pre_shared_key** Det faktiska PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="a87cb-298">**psk_length** PSK-värdets längd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="a87cb-299">**psk_identity** En sträng som används för att identifiera det här PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="a87cb-300">**identity_length** PSK-identitetens längd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="a87cb-301">**tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.</span><span class="sxs-lookup"><span data-stu-id="a87cb-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="a87cb-302">**hint_length** Längden på tips strängen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-303">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-303">Return Values</span></span>

- <span data-ttu-id="a87cb-304">**NX_SUCCESS** (0x00) tillägget av PSK lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="a87cb-305">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.</span><span class="sxs-lookup"><span data-stu-id="a87cb-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-307">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-307">Allowed From</span></span>

<span data-ttu-id="a87cb-308">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-309">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-310">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-310">See Also</span></span>

- <span data-ttu-id="a87cb-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="a87cb-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="a87cb-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="a87cb-317">Initierar NetX Secure TLS-modulen</span><span class="sxs-lookup"><span data-stu-id="a87cb-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-318">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="a87cb-319">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-319">Description</span></span>

<span data-ttu-id="a87cb-320">Den här tjänsten initierar NetX Secure TLS-modulen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="a87cb-321">Det måste anropas innan andra NetX-säkra tjänster kan nås.</span><span class="sxs-lookup"><span data-stu-id="a87cb-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-322">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-322">Parameters</span></span>

<span data-ttu-id="a87cb-323">Ingen</span><span class="sxs-lookup"><span data-stu-id="a87cb-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-324">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-324">Return Values</span></span>

<span data-ttu-id="a87cb-325">Inget</span><span class="sxs-lookup"><span data-stu-id="a87cb-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-326">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-326">Allowed From</span></span>

<span data-ttu-id="a87cb-327">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a87cb-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-328">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="a87cb-329">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-329">See Also</span></span>

- <span data-ttu-id="a87cb-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="a87cb-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="a87cb-332">Lägg till ett lokalt certifikat till NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-334">Description</span></span>

<span data-ttu-id="a87cb-335">Den här tjänsten lägger till en initierad NX_SECURE_X509_CERT struktur instans i det lokala arkivet i en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="a87cb-336">Det här certifikatet kan användas av TLS-stacken för att identifiera enheten under TLS-handskakningen (om den har marker ATS som ett identitets certifikat när certifikat strukturen initierades med nx_secure_x509_certificate_initialize) eller som en utfärdare som en del av en certifikat kedja som tillhandahölls till fjärrvärden under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="a87cb-337">Om flera lokala certifikat med samma namn krävs kan certifikat läggas till med hjälp av *nx_secure_tls_server_certificate_add* tjänsten (se varning nedan).</span><span class="sxs-lookup"><span data-stu-id="a87cb-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="a87cb-338">Ett certifikat **krävs** för TLS-server läge.</span><span class="sxs-lookup"><span data-stu-id="a87cb-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="a87cb-339">Ett certifikat är *valfritt* för TLS-klient läge.</span><span class="sxs-lookup"><span data-stu-id="a87cb-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-340">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Server certifikatets API använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på det 509-namn som används i X. De lokala certifikat tjänsterna är ett bekvämt alternativ till den numeriska identifieraren för program som bara använder ett enda identitets certifikat – genom att använda det egna namnet behöver programmet inte hålla koll på numeriska identifierare.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-341">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-341">Parameters</span></span>

- <span data-ttu-id="a87cb-342">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-343">**certificate_ptr** Pekar mot en initierad TLS-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-344">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-344">Return Values</span></span>

- <span data-ttu-id="a87cb-345">**NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="a87cb-346">**NX_INVALID_PARAMETERS** (0X4D) försökte lägga till ett ogiltigt eller duplicerat certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="a87cb-347">**NX_PTR_ERROR** (0X07) ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-348">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-348">Allowed From</span></span>

<span data-ttu-id="a87cb-349">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-350">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-351">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-351">See Also</span></span>

- <span data-ttu-id="a87cb-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="a87cb-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="a87cb-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="a87cb-358">Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn</span><span class="sxs-lookup"><span data-stu-id="a87cb-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-359">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="a87cb-360">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-360">Description</span></span>

<span data-ttu-id="a87cb-361">Den här tjänsten hittar ett certifikat i certifikat arkivet för den lokala enheten för en TLS-session och returnerar en pekare till NX_SECURE_X509_CERT strukturen i arkivet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="a87cb-362">Common_name-parametern och dess längd (name_length) används för att identifiera certifikatet i arkivet genom att matcha certifikatets namn för fältet X. 509 subject.</span><span class="sxs-lookup"><span data-stu-id="a87cb-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="a87cb-363">Om det finns mer än ett certifikat med samma egna namn kommer endast det första att returneras – Använd *nx_secure_tls_server_certificate_find* i stället.</span><span class="sxs-lookup"><span data-stu-id="a87cb-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-364">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Server certifikatets API använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på det 509-namn som används i X. De lokala certifikat tjänsterna är ett bekvämt alternativ till den numeriska identifieraren för program som bara använder ett enda identitets certifikat – genom att använda det egna namnet behöver programmet inte hålla koll på numeriska identifierare.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-365">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-365">Parameters</span></span>

- <span data-ttu-id="a87cb-366">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-367">**certifikat** Returnera pekare till matchat certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="a87cb-368">**common_name** Gemensam namn sträng som ska matchas (DNS-namn).</span><span class="sxs-lookup"><span data-stu-id="a87cb-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="a87cb-369">**name_length** Längden på common_name sträng data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-370">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-370">Return Values</span></span>

- <span data-ttu-id="a87cb-371">**NX_SUCCESS** (0X00) certifikat hittades och pekaren returnerades i "Certificate"-parametern.</span><span class="sxs-lookup"><span data-stu-id="a87cb-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="a87cb-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat med det angivna nätverks namnet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="a87cb-373">**NX_PTR_ERROR** (0X07) ogiltig TLS-session, certifikat pekare eller gemensam namn sträng.</span><span class="sxs-lookup"><span data-stu-id="a87cb-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-374">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-374">Allowed From</span></span>

<span data-ttu-id="a87cb-375">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-376">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-376">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-377">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-377">See Also</span></span>

- <span data-ttu-id="a87cb-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="a87cb-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="a87cb-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="a87cb-384">Ta bort det lokala certifikatet från NetX Secure TLS-sessionen</span><span class="sxs-lookup"><span data-stu-id="a87cb-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-385">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="a87cb-386">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-386">Description</span></span>

<span data-ttu-id="a87cb-387">Den här tjänsten tar bort en lokal certifikat instans från en TLS-session, som är nyckelbaserad i fältet eget namn i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-388">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Server certifikatets API använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på det 509-namn som används i X. De lokala certifikat tjänsterna är ett bekvämt alternativ till den numeriska identifieraren för program som bara använder ett enda identitets certifikat – genom att använda det egna namnet behöver programmet inte hålla koll på numeriska identifierare.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-389">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-389">Parameters</span></span>

- <span data-ttu-id="a87cb-390">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-391">**common_name** Värdet för eget namn för det certifikat som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="a87cb-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="a87cb-392">**common_name_length** Längden på den gemensamma namn strängen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-393">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-393">Return Values</span></span>

- <span data-ttu-id="a87cb-394">**NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="a87cb-395">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-396">Det gick inte att hitta **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** -certifikat (0x119).</span><span class="sxs-lookup"><span data-stu-id="a87cb-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-397">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-397">Allowed From</span></span>

<span data-ttu-id="a87cb-398">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-399">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-400">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-400">See Also</span></span>

- <span data-ttu-id="a87cb-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="a87cb-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="a87cb-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="a87cb-406">Beräkna storleken på kryptografiska metadata för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-407">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-408">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-408">Description</span></span>

<span data-ttu-id="a87cb-409">Den här tjänsten beräknar och returnerar storleken på de kryptografiska metadata som behövs för en viss TLS-session och TLS-kryptografisk tabell (se avsnittet "initiera TLS med kryptografiska metoder" för mer information om tabellen för kryptografi kryptering).</span><span class="sxs-lookup"><span data-stu-id="a87cb-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="a87cb-410">Den här tjänsten ska anropas med önskad kryptografiska tabell för att beräkna storleken på den metadata-buffert som överfördes till nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="a87cb-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-411">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-411">Parameters</span></span>

- <span data-ttu-id="a87cb-412">**crypto_table** Pekar till en fullständig NetX Secure TLS-kryptografi tabell.</span><span class="sxs-lookup"><span data-stu-id="a87cb-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="a87cb-413">**metadata_size** Resultatet av storleks beräkningen i byte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-414">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-414">Return Values</span></span>

- <span data-ttu-id="a87cb-415">**NX_SUCCESS** (0X00) utförde beräkningen av metadata-storlek.</span><span class="sxs-lookup"><span data-stu-id="a87cb-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="a87cb-416">**NX_PTR_ERROR** (0X07) ogiltig-pekare för kryptografi tabell eller RETUR storlek.</span><span class="sxs-lookup"><span data-stu-id="a87cb-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-417">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-417">Allowed From</span></span>

<span data-ttu-id="a87cb-418">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-419">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-419">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-420">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-420">See Also</span></span>

- <span data-ttu-id="a87cb-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="a87cb-422">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="a87cb-422">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="a87cb-423">Beräkna hash-värdet för NetX säkra biblioteks rutiner</span><span class="sxs-lookup"><span data-stu-id="a87cb-423">Compute the hash value of the NetX Secure library routines</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-424">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-424">Prototype</span></span>

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a><span data-ttu-id="a87cb-425">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-425">Description</span></span>

<span data-ttu-id="a87cb-426">Den här tjänsten initierar NetX Secure TLS-modulen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-426">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="a87cb-427">Det måste anropas innan andra NetX-säkra tjänster kan nås.</span><span class="sxs-lookup"><span data-stu-id="a87cb-427">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-428">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-428">Parameters</span></span>

<span data-ttu-id="a87cb-429">Ingen</span><span class="sxs-lookup"><span data-stu-id="a87cb-429">None</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-430">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-430">Return Values</span></span>

<span data-ttu-id="a87cb-431">Inget</span><span class="sxs-lookup"><span data-stu-id="a87cb-431">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-432">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-432">Allowed From</span></span>

<span data-ttu-id="a87cb-433">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a87cb-433">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-434">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-434">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="a87cb-435">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-435">See Also</span></span>

- <span data-ttu-id="a87cb-436">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-436">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="a87cb-437">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-437">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="a87cb-438">Allokera ett paket för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-438">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-439">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-439">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a87cb-440">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-440">Description</span></span>

<span data-ttu-id="a87cb-441">Den här tjänsten allokerar en NX_PACKET för den angivna aktiva TLS-sessionen från den angivna NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="a87cb-441">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="a87cb-442">Den här tjänsten ska anropas av programmet för att allokera data paket som ska skickas via en TLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-442">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="a87cb-443">TLS-sessionen måste initieras innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-443">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="a87cb-444">Det allokerade paketet initieras korrekt så att TLS-sidhuvudet och sid fots data kan läggas till efter att paket data har fyllts i.</span><span class="sxs-lookup"><span data-stu-id="a87cb-444">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="a87cb-445">Beteendet är annars identiskt med *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-445">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-446">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-446">Parameters</span></span>

- <span data-ttu-id="a87cb-447">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-447">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-448">**pool_ptr** Pekar till en NX_PACKET_POOL som paketet ska allokeras från.</span><span class="sxs-lookup"><span data-stu-id="a87cb-448">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="a87cb-449">**packet_ptr** Utmatnings pekare till det nyligen allokerade paketet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-449">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="a87cb-450">**wait_option** Uppehålls alternativ för paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-450">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-451">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-451">Return Values</span></span>

- <span data-ttu-id="a87cb-452">**NX_SUCCESS** (0x00) paket tilldelningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-452">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="a87cb-453">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) den underliggande paket tilldelningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-453">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="a87cb-454">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-454">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-455">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-455">Allowed From</span></span>

<span data-ttu-id="a87cb-456">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-457">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-457">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-458">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-458">See Also</span></span>

- <span data-ttu-id="a87cb-459">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-459">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="a87cb-460">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-460">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-461">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-461">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-462">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-462">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-463">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-463">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-464">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-464">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-465">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-465">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-466">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-466">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="a87cb-467">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-467">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="a87cb-468">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-468">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="a87cb-469">Lägga till en i förväg delad nyckel till en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-469">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-470">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-470">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="a87cb-471">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-471">Description</span></span>

<span data-ttu-id="a87cb-472">Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett kontroll block för TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-472">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="a87cb-473">PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.</span><span class="sxs-lookup"><span data-stu-id="a87cb-473">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-474">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-474">Parameters</span></span>

- <span data-ttu-id="a87cb-475">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-475">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-476">**pre_shared_key** Det faktiska PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-476">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="a87cb-477">**psk_length** PSK-värdets längd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-477">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="a87cb-478">**psk_identity** En sträng som används för att identifiera det här PSK-värdet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-478">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="a87cb-479">**identity_length** PSK-identitetens längd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-479">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="a87cb-480">**tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.</span><span class="sxs-lookup"><span data-stu-id="a87cb-480">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="a87cb-481">**hint_length** Längden på tips strängen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-481">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-482">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-482">Return Values</span></span>

- <span data-ttu-id="a87cb-483">**NX_SUCCESS** (0x00) tillägget av PSK lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-483">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="a87cb-484">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-484">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-485">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.</span><span class="sxs-lookup"><span data-stu-id="a87cb-485">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-486">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-486">Allowed From</span></span>

<span data-ttu-id="a87cb-487">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-488">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-488">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-489">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-489">See Also</span></span>

- <span data-ttu-id="a87cb-490">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-490">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="a87cb-491">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-491">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-492">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-492">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-493">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-493">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-494">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-494">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="a87cb-495">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-495">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="a87cb-496">Allokera utrymme för certifikatet som tillhandahålls av en fjärran sluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="a87cb-496">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-497">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-497">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-498">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-498">Description</span></span>

<span data-ttu-id="a87cb-499">Den här tjänsten lägger till en oinitierad NX_SECURE_X509_CERT struktur instans till en TLS-session för att allokera utrymme för certifikat som tillhandahålls av en fjärrvärd under en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-499">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="a87cb-500">Fjärrcertifikatets data parsas av NetX Secure TLS och den informationen används för att fylla i den certifikat struktur instans som anges för den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-500">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="a87cb-501">Certifikat som läggs till på det här sättet placeras i en länkad lista.</span><span class="sxs-lookup"><span data-stu-id="a87cb-501">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="a87cb-502">Om det är förväntat att fjärrvärden ska tillhandahålla flera certifikat, ska den här funktionen anropas flera gånger för att allokera utrymme för alla certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-502">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="a87cb-503">De ytterligare certifikaten läggs till i slutet av den länkade listan över certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-503">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="a87cb-504">Om ett fjärrcertifikat inte allokeras kan ett klient läge för TLS Miss lyckas under TLS-handskakningen om inte en i förväg delad nyckel (PSK) ciphersuite används.</span><span class="sxs-lookup"><span data-stu-id="a87cb-504">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="a87cb-505">Parametern *raw_certificate_buffer* pekar på utrymmet som allokerats för att lagra det inkommande Fjärrcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-505">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="a87cb-506">Typiska certifikat med RSA-nycklar på 2048-bitar som använder SHA-256 för signaturer är i intervallet 1000-2000 byte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-506">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="a87cb-507">Bufferten bör vara tillräckligt stor för att minst innehålla den storlek som används, men beroende på vilka fjärrcertifikaten kan vara betydligt mindre eller större.</span><span class="sxs-lookup"><span data-stu-id="a87cb-507">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="a87cb-508">Observera att om bufferten är för liten för att rymma det inkommande certifikatet, avslutas TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-508">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="a87cb-509">För TLS-serverinställningar behövs endast en tilldelning av fjärrcertifikat om autentisering av klient certifikat är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-509">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-510">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-510">Parameters</span></span>

- <span data-ttu-id="a87cb-511">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-511">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-512">**certificate_ptr** Pekar mot en oinitierad X. 509-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-512">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="a87cb-513">**raw_certificate_buffer** Pekar på en buffert för att lagra det icke-parsade certifikatet som togs emot från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-513">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="a87cb-514">**raw_buffer_size** Storlek på den råa certifikatets buffert.</span><span class="sxs-lookup"><span data-stu-id="a87cb-514">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-515">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-515">Return Values</span></span>

- <span data-ttu-id="a87cb-516">**NX_SUCCESS** (0x00) allokering av certifikat har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-516">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="a87cb-517">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-517">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-518">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0X12D) den angivna bufferten var för liten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-518">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="a87cb-519">**NX_INVALID_PARAMETERS** (0X4D) försökte lägga till ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-519">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-520">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-520">Allowed From</span></span>

<span data-ttu-id="a87cb-521">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-522">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-522">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-523">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-523">See Also</span></span>

- <span data-ttu-id="a87cb-524">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="a87cb-524">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="a87cb-525">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-525">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="a87cb-526">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-526">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="a87cb-527">Allokera utrymme för alla certifikat som tillhandahålls av en fjärran sluten TLS-värd</span><span class="sxs-lookup"><span data-stu-id="a87cb-527">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-528">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-528">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-529">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-529">Description</span></span>

<span data-ttu-id="a87cb-530">Den här tjänsten allokerar utrymme för att bearbeta inkommande certifikat kedjor från fjärranslutna Server värdar för att utföra X. 509-autentisering och verifiering i en TLS-klient instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-530">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="a87cb-531">För TLS-serverinställningar behövs endast fjärrtilldelning av certifikat om klienten X. 509-certifikatautentisering är aktive rad – för TLS Server-instanser bör tjänsten *nx_secure_tls_session_x509_client_verify_configure* användas i stället.</span><span class="sxs-lookup"><span data-stu-id="a87cb-531">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="a87cb-532">Om du inte allokerar fjärrcertifikat, Miss lyckas TLS-klientens läge under TLS-handskakningen om inte en i förväg delad nyckel (PSK) ciphersuite används.</span><span class="sxs-lookup"><span data-stu-id="a87cb-532">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="a87cb-533">*Certificate_buffer* -parametern pekar på utrymme som allokerats för att lagra inkommande fjärrcertifikat och kontroll block som behövs för dessa certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-533">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="a87cb-534">Bufferten kommer att divideras med antalet certifikat (*certs_number*) med samma del som varje certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-534">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="a87cb-535">Parametern *buffer_size*  anger buffertens storlek.</span><span class="sxs-lookup"><span data-stu-id="a87cb-535">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="a87cb-536">Utrymmet som behövs hittar du i följande formel:</span><span class="sxs-lookup"><span data-stu-id="a87cb-536">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="a87cb-537">Typiska certifikat med RSA-nycklar på 2048-bitar som använder SHA-256 för signaturer är i intervallet 1000-2000 byte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-537">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="a87cb-538">Bufferten bör vara tillräckligt stor för att minst innehålla den storlek som används för varje certifikat, men beroende på fjärrdatorns certifikat kan vara betydligt mindre eller större.</span><span class="sxs-lookup"><span data-stu-id="a87cb-538">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="a87cb-539">Observera att om bufferten är för liten för att rymma det inkommande certifikatet, avslutas TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-539">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-540">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-540">Parameters</span></span>

- <span data-ttu-id="a87cb-541">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-541">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="a87cb-542">**certs_number** Antal certifikat som ska allokeras från den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-542">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="a87cb-543">**certificate_buffer** Pekar till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-543">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="a87cb-544">**buffer_size** Storlek på certifikatets buffert.</span><span class="sxs-lookup"><span data-stu-id="a87cb-544">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-545">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-545">Return Values</span></span>

- <span data-ttu-id="a87cb-546">**NX_SUCCESS** (0x00) allokering av certifikat har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-546">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="a87cb-547">**NX_PTR_ERROR** (0X07) ogiltig TLS-session eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-547">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="a87cb-548">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0X12D) den angivna bufferten var för liten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-548">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="a87cb-549">**NX_INVALID_PARAMETERS** (0X4D) bufferten var för liten för att rymma det önskade antalet certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-549">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-550">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-550">Allowed From</span></span>

<span data-ttu-id="a87cb-551">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-551">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-552">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-552">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-553">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-553">See Also</span></span>

- <span data-ttu-id="a87cb-554">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-554">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-555">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-555">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="a87cb-556">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="a87cb-556">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="a87cb-557">Ledigt utrymme allokerat för inkommande certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-557">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-558">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-558">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-559">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-559">Description</span></span>

<span data-ttu-id="a87cb-560">Den här tjänsten används för att frigöra alla certifikat-buffertar som tilldelas till en viss TLS-session genom att nx_secure_tls_remote_certificate_allocated genom att returnera dem till det lediga certifikat utrymmet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-560">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="a87cb-561">Detta kan vara nödvändigt om ett program återanvänder ett TLS-sessionsobjekt utan att ta bort det och återskapa det med nx_secure_tls_session_delete och nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="a87cb-561">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="a87cb-562">Observera att det fjärranslutna certifikat utrymmet återställs automatiskt när TLS-sessionen återställs i nx_secure_tls_session_end så att de flesta program inte behöver anropa den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-562">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-563">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-563">Parameters</span></span>

- <span data-ttu-id="a87cb-564">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-564">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-565">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-565">Return Values</span></span>

- <span data-ttu-id="a87cb-566">**NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-566">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="a87cb-567">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-567">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-568">**NX_INVALID_PARAMETERS** (0X4D) internt fel – certifikat arkivet är antagligen skadat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-568">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-569">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-569">Allowed From</span></span>

<span data-ttu-id="a87cb-570">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-571">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-571">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-572">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-572">See Also</span></span>

- <span data-ttu-id="a87cb-573">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-573">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-574">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-574">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-575">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-575">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-576">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-576">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="a87cb-577">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-577">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="a87cb-578">Lägg till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="a87cb-578">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-579">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-579">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="a87cb-580">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-580">Description</span></span>

<span data-ttu-id="a87cb-581">Den här tjänsten används för att lägga till ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med en numerisk identifierare i stället för att indexera lagret med hjälp av X. 509-ämnet (eget namn) i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-581">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="a87cb-582">Den numeriska identifieraren är separat från certifikatet och gör det möjligt att lägga till flera certifikat som identitets certifikat till en TLS-server, samt tillåta att flera certifikat med samma eget namn läggs till i samma lokala TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-582">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="a87cb-583">Samma tjänst kan användas för klient certifikat, men det är sällsynt att en TLS-klient har flera identitets certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-583">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="a87cb-584">Parametern cert_id är ett positivt heltal som inte är noll som tilldelats av programmet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-584">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="a87cb-585">Det faktiska värdet spelar ingen roll (förutom noll) men det måste vara unikt i arkivet för den angivna TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-585">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="a87cb-586">Cert_id-värdet kan användas för att söka efter och ta bort certifikat från det lokala arkivet med nx_secure_tls_server_certificate_find respektive nx_secure_tls_server_certificate_remove.</span><span class="sxs-lookup"><span data-stu-id="a87cb-586">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-587">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. Nx_secure_tls_server_certificate_add-API: et använder en unik numerisk identifierare för varje certifikat, och det lokala Certificate Services-indexet baserat på det X. 509-delade namnet. Server certifikat tjänsterna tillåter att flera certifikat med delade data (särskilt nätverks namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-587">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-588">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-588">Parameters</span></span>

- <span data-ttu-id="a87cb-589">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-589">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-590">**certifikat** Pekar till en tidigare initierad X. 509-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-590">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="a87cb-591">**cert_id** Positivt, icke-noll, relativt unikt certifikat-ID-nummer.</span><span class="sxs-lookup"><span data-stu-id="a87cb-591">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-592">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-592">Return Values</span></span>

- <span data-ttu-id="a87cb-593">**NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-593">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="a87cb-594">**NX_PTR_ERROR** (0X07) ogiltig TLS session orcertificate-pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-594">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="a87cb-595">**NX_SECURE_TLS_CERT_ID_INVALID** (0X138) det tillhandahållna certifikat-ID: t hade ett ogiltigt värde (troligen 0).</span><span class="sxs-lookup"><span data-stu-id="a87cb-595">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="a87cb-596">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0X139) det tillhandahållna certifikat-ID: t fanns redan i det lokala arkivet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-596">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="a87cb-597">**NX_INVALID_PARAMETERS (0X4D)** Internt fel – certifikat arkivet är antagligen skadat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-597">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-598">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-598">Allowed From</span></span>

<span data-ttu-id="a87cb-599">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-600">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-600">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-601">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-601">See Also</span></span>

- <span data-ttu-id="a87cb-602">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-602">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-603">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-603">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="a87cb-604">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-604">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="a87cb-605">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-605">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="a87cb-606">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-606">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="a87cb-607">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-607">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="a87cb-608">Hitta ett certifikat med en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="a87cb-608">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-609">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-609">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="a87cb-610">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-610">Description</span></span>

<span data-ttu-id="a87cb-611">Den här tjänsten används för att hitta ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med en numerisk identifierare i stället för att indexera lagret med hjälp av X. 509-ämnet (eget namn) i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-611">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="a87cb-612">Parametern cert_id är ett positivt heltal som inte är noll och som tilldelas av programmet när certifikatet läggs till i det lokala arkivet för TLS-sessionen med hjälp av nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="a87cb-612">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-613">*Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. Nx_secure_tls_server_certificate_add-API: et använder en unik numerisk identifierare för varje certifikat, och det lokala Certificate Services-indexet baserat på det X. 509-delade namnet. Server certifikat tjänsterna tillåter att flera certifikat med delade data (särskilt nätverks namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-613">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-614">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-614">Parameters</span></span>

- <span data-ttu-id="a87cb-615">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-615">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-616">**certifikat** Pekar på en X. 509-certifikat pekare för att returnera en referens till det påträffade certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-616">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="a87cb-617">**cert_id** Positivt värde för certifikat-ID som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="a87cb-617">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-618">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-618">Return Values</span></span>

- <span data-ttu-id="a87cb-619">**NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-619">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="a87cb-620">**NX_PTR_ERROR** (0X07) ogiltig TLS-session eller certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-620">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="a87cb-621">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) det angivna certifikat-ID: t matchade inte några i det lokala arkivet i den angivna TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-621">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-622">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-622">Allowed From</span></span>

<span data-ttu-id="a87cb-623">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-623">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-624">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-624">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-625">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-625">See Also</span></span>

- <span data-ttu-id="a87cb-626">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-626">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-627">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-627">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="a87cb-628">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-628">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="a87cb-629">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-629">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="a87cb-630">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-630">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="a87cb-631">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-631">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="a87cb-632">Ta bort ett lokalt Server certifikat med en numerisk identifierare</span><span class="sxs-lookup"><span data-stu-id="a87cb-632">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-633">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-633">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="a87cb-634">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-634">Description</span></span>

<span data-ttu-id="a87cb-635">Den här tjänsten används för att ta bort ett certifikat från en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med en numerisk identifierare i stället för att indexera lagret med hjälp av X. 509-ämnet (eget namn) i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-635">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="a87cb-636">Parametern cert_id är ett positivt heltal som inte är noll och som tilldelas av programmet när certifikatet läggs till i det lokala arkivet för TLS-sessionen med hjälp av nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="a87cb-636">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-637">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-637">Parameters</span></span>

- <span data-ttu-id="a87cb-638">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-638">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-639">**cert_id** Positivt värde för certifikat-ID som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="a87cb-639">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-640">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-640">Return Values</span></span>

- <span data-ttu-id="a87cb-641">**NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-641">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="a87cb-642">**NX_PTR_ERROR** (0X07) ogiltig TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-642">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="a87cb-643">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) det angivna certifikat-ID: t matchade inte några i det lokala arkivet i den angivna TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-643">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-644">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-644">Allowed From</span></span>

<span data-ttu-id="a87cb-645">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-645">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-646">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-646">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-647">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-647">See Also</span></span>

- <span data-ttu-id="a87cb-648">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-648">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-649">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-649">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="a87cb-650">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-650">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="a87cb-651">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-651">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="a87cb-652">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-652">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="a87cb-653">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="a87cb-653">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="a87cb-654">Hämta TLS-avisering svärdet och nivån som skickas av den fjärranslutna värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-654">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-655">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-655">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="a87cb-656">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-656">Description</span></span>

<span data-ttu-id="a87cb-657">Den här tjänsten används för att hämta TLS-aviserings nivån och värdet när fjärrvärden skickar en avisering som svar på ett problem eller fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-657">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="a87cb-658">Värdena för parametrarna alert_level och alert_value är bara giltiga om den här funktionen anropas omedelbart efter ett TLS API-anrop som returnerade statusen NX_SECURE_TLS_ALERT_RECEIVED (0x114) som indikerar att en avisering togs emot från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-658">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="a87cb-659">Observera att om den lokala värd-TLS skickar en avisering, är de returnerade fel koderna mycket mer beskrivande av det faktiska felet än TLS-aviseringen, eftersom TLS-aviserings värden oavsiktligt utelämnas för att förhindra vissa typer av angrepp (t. ex. ett "utfyllnad för Oracle"-angrepp eller liknande).</span><span class="sxs-lookup"><span data-stu-id="a87cb-659">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="a87cb-660">Aviserings nivån har bara ett av två värden: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) eller NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="a87cb-660">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="a87cb-661">I allmänhet får endast CloseNotify-aviseringen (som används för att visa en lyckad slut punkt till en TLS-session) en nivå av "varning", även om vissa konfigurations situationer för tillägg också kan anses vara varningar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-661">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="a87cb-662">De flesta aviseringar är "oåterkallelig" som indikerar ett potentiellt säkerhets fel och som resulterar i omedelbar avslutning av TLS-anslutningen (hand skakning eller session).</span><span class="sxs-lookup"><span data-stu-id="a87cb-662">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="a87cb-663">TLS-aviseringens värden definieras i TLS-rapporterna, här är listan från RFC 5246 (TLSv 1.2) som referens:</span><span class="sxs-lookup"><span data-stu-id="a87cb-663">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="a87cb-664">Aviseringsnamn</span><span class="sxs-lookup"><span data-stu-id="a87cb-664">Alert Name</span></span>                     | <span data-ttu-id="a87cb-665">Värde</span><span class="sxs-lookup"><span data-stu-id="a87cb-665">Value</span></span> | <span data-ttu-id="a87cb-666">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-666">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a87cb-667">close_notify</span><span class="sxs-lookup"><span data-stu-id="a87cb-667">close_notify</span></span>                  | <span data-ttu-id="a87cb-668">0</span><span class="sxs-lookup"><span data-stu-id="a87cb-668">0</span></span>     | <span data-ttu-id="a87cb-669">Inget fel, indikerar lyckad session slut</span><span class="sxs-lookup"><span data-stu-id="a87cb-669">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="a87cb-670">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="a87cb-670">unexpected_message</span></span>            | <span data-ttu-id="a87cb-671">10</span><span class="sxs-lookup"><span data-stu-id="a87cb-671">10</span></span>    | <span data-ttu-id="a87cb-672">TLS tog emot ett oväntat eller meddelande som inte är i ordning</span><span class="sxs-lookup"><span data-stu-id="a87cb-672">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="a87cb-673">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="a87cb-673">bad_record_mac</span></span>               | <span data-ttu-id="a87cb-674">20</span><span class="sxs-lookup"><span data-stu-id="a87cb-674">20</span></span>    | <span data-ttu-id="a87cb-675">Dekryptering och/eller MAC-verifiering misslyckades</span><span class="sxs-lookup"><span data-stu-id="a87cb-675">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="a87cb-676">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="a87cb-676">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="a87cb-677">21</span><span class="sxs-lookup"><span data-stu-id="a87cb-677">21</span></span>    | <span data-ttu-id="a87cb-678">**Föråldrad** Det gick inte att dekryptera (inaktuellt på grund av att Oracle-attacker för utfyllnad)</span><span class="sxs-lookup"><span data-stu-id="a87cb-678">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="a87cb-679">record_overflow</span><span class="sxs-lookup"><span data-stu-id="a87cb-679">record_overflow</span></span>               | <span data-ttu-id="a87cb-680">22</span><span class="sxs-lookup"><span data-stu-id="a87cb-680">22</span></span>    | <span data-ttu-id="a87cb-681">En post som är större än den största tillåtna storleken för TLS-data har tagits emot</span><span class="sxs-lookup"><span data-stu-id="a87cb-681">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="a87cb-682">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="a87cb-682">decompression_failure</span></span>         | <span data-ttu-id="a87cb-683">30</span><span class="sxs-lookup"><span data-stu-id="a87cb-683">30</span></span>    | <span data-ttu-id="a87cb-684">Ett problem påträffades vid komprimering/expandering av en TLS-post</span><span class="sxs-lookup"><span data-stu-id="a87cb-684">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="a87cb-685">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="a87cb-685">handshake_failure</span></span>             | <span data-ttu-id="a87cb-686">40</span><span class="sxs-lookup"><span data-stu-id="a87cb-686">40</span></span>    | <span data-ttu-id="a87cb-687">Ett ospecificerat hand skaknings fel inträffade som inte omfattas av en annan avisering</span><span class="sxs-lookup"><span data-stu-id="a87cb-687">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="a87cb-688">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="a87cb-688">no_certificate_RESERVED</span></span>      | <span data-ttu-id="a87cb-689">41</span><span class="sxs-lookup"><span data-stu-id="a87cb-689">41</span></span>    | <span data-ttu-id="a87cb-690">**Föråldrad** i TLS (endast SSL)</span><span class="sxs-lookup"><span data-stu-id="a87cb-690">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="a87cb-691">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="a87cb-691">bad_certificate</span></span>               | <span data-ttu-id="a87cb-692">42</span><span class="sxs-lookup"><span data-stu-id="a87cb-692">42</span></span>    | <span data-ttu-id="a87cb-693">Ett certifikat som tagits emot innehöll ogiltig formatering eller signaturer</span><span class="sxs-lookup"><span data-stu-id="a87cb-693">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="a87cb-694">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="a87cb-694">unsupported_certificate</span></span>       | <span data-ttu-id="a87cb-695">43</span><span class="sxs-lookup"><span data-stu-id="a87cb-695">43</span></span>    | <span data-ttu-id="a87cb-696">Ett certifikat togs emot som har en ogiltig typ (t. ex. endast signerings certifikat som används för TLS-serverautentisering)</span><span class="sxs-lookup"><span data-stu-id="a87cb-696">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="a87cb-697">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="a87cb-697">certificate_revoked</span></span>           | <span data-ttu-id="a87cb-698">44</span><span class="sxs-lookup"><span data-stu-id="a87cb-698">44</span></span>    | <span data-ttu-id="a87cb-699">Certifikat statusen (som anges av en CRL eller OCSP) indikeras som "återkallad"</span><span class="sxs-lookup"><span data-stu-id="a87cb-699">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="a87cb-700">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="a87cb-700">certificate_expired</span></span>           | <span data-ttu-id="a87cb-701">45</span><span class="sxs-lookup"><span data-stu-id="a87cb-701">45</span></span>    | <span data-ttu-id="a87cb-702">Det mottagna certifikatet var utanför det giltiga datum intervallet (antingen inte giltigt ännu eller har gått ut)</span><span class="sxs-lookup"><span data-stu-id="a87cb-702">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="a87cb-703">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="a87cb-703">certificate_unknown</span></span>           | <span data-ttu-id="a87cb-704">46</span><span class="sxs-lookup"><span data-stu-id="a87cb-704">46</span></span>    | <span data-ttu-id="a87cb-705">Vissa okända certifikat problem påträffades som inte omfattas av andra aviseringar</span><span class="sxs-lookup"><span data-stu-id="a87cb-705">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="a87cb-706">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="a87cb-706">illegal_parameter</span></span>             | <span data-ttu-id="a87cb-707">47</span><span class="sxs-lookup"><span data-stu-id="a87cb-707">47</span></span>    | <span data-ttu-id="a87cb-708">En del konfiguration eller förhandlat värde i TLS-handskakningen var ogiltigt eller utanför intervallet</span><span class="sxs-lookup"><span data-stu-id="a87cb-708">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="a87cb-709">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="a87cb-709">unknown_ca</span></span>                    | <span data-ttu-id="a87cb-710">48</span><span class="sxs-lookup"><span data-stu-id="a87cb-710">48</span></span>    | <span data-ttu-id="a87cb-711">Mottaget identitets certifikat kunde inte spåras via en certifikat kedja till ett betrott rot certifikat för certifikat utfärdare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-711">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="a87cb-712">access_denied</span><span class="sxs-lookup"><span data-stu-id="a87cb-712">access_denied</span></span>                 | <span data-ttu-id="a87cb-713">49</span><span class="sxs-lookup"><span data-stu-id="a87cb-713">49</span></span>    | <span data-ttu-id="a87cb-714">Anger att ett giltigt certifikat togs emot men program åtkomst kontrollen angav att certifikatet inte var giltigt för de begärda resurserna.</span><span class="sxs-lookup"><span data-stu-id="a87cb-714">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="a87cb-715">decode_error</span><span class="sxs-lookup"><span data-stu-id="a87cb-715">decode_error</span></span>                  | <span data-ttu-id="a87cb-716">50</span><span class="sxs-lookup"><span data-stu-id="a87cb-716">50</span></span>    | <span data-ttu-id="a87cb-717">Ett fält eller värde i ett TLS-huvud eller hand skaknings meddelande låg utanför intervallet eller är ogiltigt, vilket ledde till ett fel vid avkodning av en TLS-post.</span><span class="sxs-lookup"><span data-stu-id="a87cb-717">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="a87cb-718">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="a87cb-718">decrypt_error</span></span>                 | <span data-ttu-id="a87cb-719">51</span><span class="sxs-lookup"><span data-stu-id="a87cb-719">51</span></span>    | <span data-ttu-id="a87cb-720">Det gick inte att verifiera en signatur eller en färdig meddelande-hash under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-720">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="a87cb-721">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="a87cb-721">export_restriction_RESERVED</span></span>  | <span data-ttu-id="a87cb-722">60</span><span class="sxs-lookup"><span data-stu-id="a87cb-722">60</span></span>    | <span data-ttu-id="a87cb-723">Föråldrad i TLSv 1.2</span><span class="sxs-lookup"><span data-stu-id="a87cb-723">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="a87cb-724">protocol_version</span><span class="sxs-lookup"><span data-stu-id="a87cb-724">protocol_version</span></span>              | <span data-ttu-id="a87cb-725">70</span><span class="sxs-lookup"><span data-stu-id="a87cb-725">70</span></span>    | <span data-ttu-id="a87cb-726">Den TLS-protokollversion som förhandlas under hand skakningen känns igen men stöds inte (t. ex. TLSv 1.0 har presenter ATS men inte Aktiver ATS).</span><span class="sxs-lookup"><span data-stu-id="a87cb-726">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="a87cb-727">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="a87cb-727">insufficient_security</span></span>         | <span data-ttu-id="a87cb-728">71</span><span class="sxs-lookup"><span data-stu-id="a87cb-728">71</span></span>    | <span data-ttu-id="a87cb-729">Skickas varje gång en hand skakning Miss lyckas på grund av att det inte finns några säkra chiffer (till exempel att nyckel storleken är för liten för program kraven)</span><span class="sxs-lookup"><span data-stu-id="a87cb-729">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="a87cb-730">internal_error</span><span class="sxs-lookup"><span data-stu-id="a87cb-730">internal_error</span></span>                | <span data-ttu-id="a87cb-731">80</span><span class="sxs-lookup"><span data-stu-id="a87cb-731">80</span></span>    | <span data-ttu-id="a87cb-732">Vissa icke-TLS-fel (t. ex. problem med minnesallokering, program problem) uppstod i en bruten TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-732">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="a87cb-733">user_canceled</span><span class="sxs-lookup"><span data-stu-id="a87cb-733">user_canceled</span></span>                 | <span data-ttu-id="a87cb-734">90</span><span class="sxs-lookup"><span data-stu-id="a87cb-734">90</span></span>    | <span data-ttu-id="a87cb-735">Returneras om TLS-sessionen avbryts av en användare eller ett program innan hand skakningen är slutförd (liknar CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="a87cb-735">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="a87cb-736">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="a87cb-736">no_renegotiation</span></span>              | <span data-ttu-id="a87cb-737">100</span><span class="sxs-lookup"><span data-stu-id="a87cb-737">100</span></span>   | <span data-ttu-id="a87cb-738">Indiates att den fjärranslutna värddatorn inte kan utföra en TLS renegotiation-handskakning som svar på en begäran om omförhandling.</span><span class="sxs-lookup"><span data-stu-id="a87cb-738">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="a87cb-739">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="a87cb-739">unsupported_extension</span></span>         | <span data-ttu-id="a87cb-740">110</span><span class="sxs-lookup"><span data-stu-id="a87cb-740">110</span></span>   | <span data-ttu-id="a87cb-741">Skickas om en TLS-klient tar emot en ServerHello som innehåller tillägg som inte uttryckligen efterfrågats i den inledande sitt hälsnings (vilket indikerar att servern har problem).</span><span class="sxs-lookup"><span data-stu-id="a87cb-741">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="a87cb-742">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-742">Parameters</span></span>

- <span data-ttu-id="a87cb-743">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-743">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-744">**alert_level** Returnera nivån för den mottagna aviseringen (varning eller allvarligt).</span><span class="sxs-lookup"><span data-stu-id="a87cb-744">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="a87cb-745">**alert_value** Returnera värdet för den mottagna aviseringen (se tabellen).</span><span class="sxs-lookup"><span data-stu-id="a87cb-745">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-746">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-746">Return Values</span></span>

- <span data-ttu-id="a87cb-747">**NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-747">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="a87cb-748">**NX_PTR_ERROR** (0X07) ogiltig TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-748">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-749">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-749">Allowed From</span></span>

<span data-ttu-id="a87cb-750">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-750">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-751">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-751">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-752">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-752">See Also</span></span>

- <span data-ttu-id="a87cb-753">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-753">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-754">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-754">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-755">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-755">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="a87cb-756">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-756">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="a87cb-757">Konfigurera en motringning för TLS som ska användas för ytterligare certifikat validering</span><span class="sxs-lookup"><span data-stu-id="a87cb-757">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-758">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-758">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="a87cb-759">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-759">Description</span></span>

<span data-ttu-id="a87cb-760">Den här tjänsten tilldelar en-funktions pekare till en TLS-session som TLS kommer att anropa när ett certifikat tas emot från en fjärrvärd, så att programmet kan utföra verifierings kontroller, till exempel DNS-validering, certifikat återkallning och tillämpning av certifikat principer.</span><span class="sxs-lookup"><span data-stu-id="a87cb-760">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="a87cb-761">NetX Secure TLS utför grundläggande X. 509-sökvägar på certifikatet innan återanropet anropas för att säkerställa att certifikatet kan spåras till ett certifikat i det betrodda TLS-certifikatarkivet, men alla andra verifieringar hanteras av återanropet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-761">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="a87cb-762">Återanropet innehåller TLS-sessionens pekare och en pekare till fjärrvärdets identitets certifikat (löv i certifikat kedjan).</span><span class="sxs-lookup"><span data-stu-id="a87cb-762">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="a87cb-763">Återanropet ska returnera NX_SUCCESS om all verifiering lyckas, annars bör den returnera en felkod som indikerar verifierings felet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-763">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="a87cb-764">Ett annat värde än NX_SUCCESS gör att TLS-handskakningen avbryts omedelbart.</span><span class="sxs-lookup"><span data-stu-id="a87cb-764">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-765">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-765">Parameters</span></span>

- <span data-ttu-id="a87cb-766">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-766">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-767">**func_ptr** Pekar mot funktionen motringning för certifikat validering.</span><span class="sxs-lookup"><span data-stu-id="a87cb-767">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-768">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-768">Return Values</span></span>

- <span data-ttu-id="a87cb-769">**NX_SUCCESS** (0x00) allokering av funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-769">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="a87cb-770">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-770">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-771">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-771">Allowed From</span></span>

<span data-ttu-id="a87cb-772">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-773">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-773">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-774">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-774">See Also</span></span>

- <span data-ttu-id="a87cb-775">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-775">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-776">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-776">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="a87cb-777">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-777">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="a87cb-778">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-778">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="a87cb-779">Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-klient hand skakning</span><span class="sxs-lookup"><span data-stu-id="a87cb-779">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-780">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-780">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="a87cb-781">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-781">Description</span></span>

<span data-ttu-id="a87cb-782">Den här tjänsten tilldelar en-funktions pekare till en TLS-session som TLS kommer att anropa när en TLS-klients hand skakning har tagit emot ett ServerHelloDone-meddelande.</span><span class="sxs-lookup"><span data-stu-id="a87cb-782">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="a87cb-783">Funktionen motringning gör att ett program kan bearbeta alla TLS-tillägg från det mottagna ServerHello-meddelandet som kräver indatamängds-eller besluts fattande.</span><span class="sxs-lookup"><span data-stu-id="a87cb-783">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="a87cb-784">Återanropet körs med inaktive ring av TLS-sessionens kontroll block och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-784">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="a87cb-785">Matrisen med tilläggs objekt är avsedd att skickas till en hjälp funktion som söker efter och tolkar ett särskilt tillägg.</span><span class="sxs-lookup"><span data-stu-id="a87cb-785">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="a87cb-786">För närvarande finns det inga specifika tillägg som stöds i NetX säkra som kräver indataport av TLS-klienten, men motringningen är tillgänglig för programkonstruktörer för att hantera anpassade eller nya tillägg som kan bli tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="a87cb-786">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="a87cb-787">En exempel hjälp funktion som analyserar TLS-tillägg som finns i Hello-meddelanden finns *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-787">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="a87cb-788">Klient återanrop kan också användas för att välja det aktiva identitets certifikatet med *nx_secure_tls_active_certificate_set* för TLS-klienten i händelse av att fjärrservern har begärt ett certifikat och angett information för att tillåta TLS-klienten att välja ett särskilt certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-788">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="a87cb-789">Mer information finns i referensen för nx_secure_tls_active_certificate_set.</span><span class="sxs-lookup"><span data-stu-id="a87cb-789">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-790">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-790">Parameters</span></span>

- <span data-ttu-id="a87cb-791">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-791">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-792">**func_ptr** Pekar mot funktionen motringning i TLS-klienten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-792">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-793">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-793">Return Values</span></span>

- <span data-ttu-id="a87cb-794">**NX_SUCCESS** (0x00) allokering av funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-794">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="a87cb-795">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-795">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-796">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-796">Allowed From</span></span>

<span data-ttu-id="a87cb-797">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-797">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-798">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-798">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-799">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-799">See Also</span></span>

- <span data-ttu-id="a87cb-800">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-800">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-801">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-801">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="a87cb-802">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-802">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="a87cb-803">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="a87cb-803">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="a87cb-804">Aktivera client X. 509-verifiering och allokera utrymme för klient certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-804">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-805">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-805">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-806">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-806">Description</span></span>

<span data-ttu-id="a87cb-807">Den här tjänsten aktiverar den valfria klientautentisering för X. 509 för en TLS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-807">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="a87cb-808">Den allokerar också utrymmet som krävs för att bearbeta inkommande certifikat kedjor från den fjärranslutna klient värden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-808">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="a87cb-809">De certifikat som anges av fjärrklienten verifieras mot betrodda certifikat för TLS-serverinstansen, tilldelade till tjänsten *nx_secure_tls_trusted_certificate_add.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-809">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="a87cb-810">För TLS-klientcertifikat krävs fjärrtilldelning av certifikat och tjänsten *nx_secure_tls_remote_certificate_buffer_allocate* ska användas i stället.</span><span class="sxs-lookup"><span data-stu-id="a87cb-810">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="a87cb-811">Att aktivera X. 509-klientautentisering på en TLS-klientsession har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-811">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="a87cb-812">*Certificate_buffer* -parametern pekar på utrymme som allokerats för att lagra inkommande fjärrcertifikat och kontroll block som behövs för dessa certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-812">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="a87cb-813">Bufferten kommer att divideras med antalet certifikat (*certs_number*) med samma del som varje certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-813">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="a87cb-814">Parametern *buffer_size* anger buffertens storlek.</span><span class="sxs-lookup"><span data-stu-id="a87cb-814">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="a87cb-815">Utrymmet som behövs hittar du i följande formel:</span><span class="sxs-lookup"><span data-stu-id="a87cb-815">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="a87cb-816">Typiska certifikat med RSA-nycklar på 2048-bitar som använder SHA-256 för signaturer är i intervallet 1000-2000 byte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-816">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="a87cb-817">Bufferten bör vara tillräckligt stor för att minst innehålla den storlek som används för varje certifikat, men beroende på fjärrdatorns certifikat kan vara betydligt mindre eller större.</span><span class="sxs-lookup"><span data-stu-id="a87cb-817">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="a87cb-818">Observera att om bufferten är för liten för att rymma det inkommande certifikatet, avslutas TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-818">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-819">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-819">Parameters</span></span>

- <span data-ttu-id="a87cb-820">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-820">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-821">**certs_number** Antal certifikat som ska allokeras från den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-821">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="a87cb-822">**certificate_buffer** Pekar till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-822">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="a87cb-823">**buffer_size** Storlek på certifikatets buffert.</span><span class="sxs-lookup"><span data-stu-id="a87cb-823">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-824">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-824">Return Values</span></span>

- <span data-ttu-id="a87cb-825">**NX_SUCCESS** (0x00) allokering av certifikat har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-825">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="a87cb-826">**NX_PTR_ERROR** (0X07) ogiltig TLS-session eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-826">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="a87cb-827">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0X12D) den angivna bufferten var för liten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-827">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="a87cb-828">**NX_INVALID_PARAMETERS** (0X4D) bufferten var för liten för att rymma det önskade antalet certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-828">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-829">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-829">Allowed From</span></span>

<span data-ttu-id="a87cb-830">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-830">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-831">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-831">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-832">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-832">See Also</span></span>

- <span data-ttu-id="a87cb-833">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-833">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-834">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-834">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-835">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-835">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="a87cb-836">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="a87cb-836">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="a87cb-837">Inaktivera autentisering av klient certifikat för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-837">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-838">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-838">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-839">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-839">Description</span></span>

<span data-ttu-id="a87cb-840">Den här tjänsten inaktiverar autentisering av klient certifikat för en angiven TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-840">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="a87cb-841">Se nx_secure_tls_session_client_verify_enable för mer information.</span><span class="sxs-lookup"><span data-stu-id="a87cb-841">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-842">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-842">Parameters</span></span>

- <span data-ttu-id="a87cb-843">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-843">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-844">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-844">Return Values</span></span>

- <span data-ttu-id="a87cb-845">**NX_SUCCESS** (0x00) status ändring har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-845">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="a87cb-846">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-846">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-847">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-847">Allowed From</span></span>

<span data-ttu-id="a87cb-848">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-848">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-849">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-849">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-850">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-850">See Also</span></span>

- <span data-ttu-id="a87cb-851">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="a87cb-851">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="a87cb-852">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-852">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-853">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-853">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="a87cb-854">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="a87cb-854">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="a87cb-855">Aktivera autentisering av klient certifikat för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-855">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-856">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-856">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-857">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-857">Description</span></span>

<span data-ttu-id="a87cb-858">Den här tjänsten aktiverar autentisering av klient certifikat för en angiven TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-858">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="a87cb-859">Om du aktiverar autentisering av klient certifikat för en TLS-serverinstans kan TLS-servern begära ett certifikat från valfri fjärran sluten TLS-klient under den första TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-859">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="a87cb-860">Certifikatet som togs emot från fjärr-TLS-klienten åtföljs av ett CertificateVerify-meddelande som TLS-servern använder för att kontrol lera att klienten äger certifikatet (har åtkomst till den privata nyckel som är kopplad till certifikatet).</span><span class="sxs-lookup"><span data-stu-id="a87cb-860">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="a87cb-861">Om det tillhandahållna certifikatet kan verifieras och spåras tillbaka till ett certifikat i det betrodda certifikat arkivet i TLS-servern via en X. 509-certifikat kedja, autentiseras fjärr-TLS-klienten och hand skakningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="a87cb-861">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="a87cb-862">Om det uppstår fel vid bearbetning av certifikatet eller CertificateVerify-meddelandet slutar TLS-handskakningen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-862">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="a87cb-863">*TLS-servern måste ha minst ett certifikat i det betrodda arkivet som har lagts till med nx_secure_tls_trusted_certificate_add eller autentiseringen fungerar alltid.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-863">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-864">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-864">Parameters</span></span>

- <span data-ttu-id="a87cb-865">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-865">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-866">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-866">Return Values</span></span>

- <span data-ttu-id="a87cb-867">**NX_SUCCESS** (0x00) status ändring har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-867">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="a87cb-868">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-868">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-869">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-869">Allowed From</span></span>

<span data-ttu-id="a87cb-870">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-871">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-871">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-872">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-872">See Also</span></span>

- <span data-ttu-id="a87cb-873">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="a87cb-873">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="a87cb-874">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-874">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-875">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-875">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-876">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-876">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="a87cb-877">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-877">nx_secure_tls_session_create</span></span>

<span data-ttu-id="a87cb-878">Skapa en NetX Secure TLS-session för säker kommunikation</span><span class="sxs-lookup"><span data-stu-id="a87cb-878">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-879">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-879">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-880">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-880">Description</span></span>

<span data-ttu-id="a87cb-881">Den här tjänsten initierar en NX_SECURE_TLS_SESSION struktur instans som ska användas för att upprätta säker TLS-kommunikation över en nätverks anslutning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-881">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="a87cb-882">Metoden tar ett NX_SECURE_TLS_CRYPTO-objekt som är ifyllt med de tillgängliga kryptografiska metoder som ska användas för TLS.</span><span class="sxs-lookup"><span data-stu-id="a87cb-882">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="a87cb-883">*Encryption_metadata_area* pekar på en buffert som tilldelats för användning av TLS för "metadata" som används av kryptografiska metoder i NX_SECURE_TLS_CRYPTOs tabellen för beräkningar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-883">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="a87cb-884">Tabellens storlek kan fastställas med hjälp av nx_secure_tls_metadata_size_calculate tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-884">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="a87cb-885">Mer information finns i avsnittet "kryptografi i NetX Secure TLS" i kapitel 3.</span><span class="sxs-lookup"><span data-stu-id="a87cb-885">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-886">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-886">Parameters</span></span>

- <span data-ttu-id="a87cb-887">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-887">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-888">**cipher_table** Pekare till TLS-kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="a87cb-888">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="a87cb-889">**encryption_metadata_area** Pekar på plats för kryptografiska metadata.</span><span class="sxs-lookup"><span data-stu-id="a87cb-889">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="a87cb-890">**encryption_metadata_size** Storlek på bufferten för metadata.</span><span class="sxs-lookup"><span data-stu-id="a87cb-890">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-891">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-891">Return Values</span></span>

- <span data-ttu-id="a87cb-892">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-892">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-893">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-893">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="a87cb-894">**NX_INVALID_PARAMETERS** (0X4D) metadata-bufferten var för liten för de metoder som angavs.</span><span class="sxs-lookup"><span data-stu-id="a87cb-894">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="a87cb-895">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) en obligatorisk cipher-metod för den aktiverade versionen av TLS angavs inte i tabellen Cipher.</span><span class="sxs-lookup"><span data-stu-id="a87cb-895">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-896">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-896">Allowed From</span></span>

<span data-ttu-id="a87cb-897">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-897">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-898">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-898">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-899">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-899">See Also</span></span>

- <span data-ttu-id="a87cb-900">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-900">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-901">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="a87cb-901">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="a87cb-902">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-902">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-903">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-903">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-904">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-904">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="a87cb-905">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-905">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-906">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-906">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-907">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-907">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-908">Kryptografi i NetX Secure TLS i kapitel 3</span><span class="sxs-lookup"><span data-stu-id="a87cb-908">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="a87cb-909">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-909">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="a87cb-910">Ta bort en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-910">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-911">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-911">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-912">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-912">Description</span></span>

<span data-ttu-id="a87cb-913">Den här tjänsten tar bort en TLS-session som representeras av en NX_SECURE_TLS_SESSIONs struktur instans och frigör alla system resurser som ägs av den sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-913">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-914">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-914">Parameters</span></span>

- <span data-ttu-id="a87cb-915">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-915">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-916">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-916">Return Values</span></span>

- <span data-ttu-id="a87cb-917">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-917">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-918">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-918">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-919">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-919">Allowed From</span></span>

<span data-ttu-id="a87cb-920">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-920">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-921">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-921">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-922">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-922">See Also</span></span>

- <span data-ttu-id="a87cb-923">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-923">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-924">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-924">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-925">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-925">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-926">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-926">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="a87cb-927">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-927">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-928">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-928">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-929">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-929">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="a87cb-930">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-930">nx_secure_tls_session_end</span></span>

<span data-ttu-id="a87cb-931">Avsluta en aktiv NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-931">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-932">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-932">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a87cb-933">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-933">Description</span></span>

<span data-ttu-id="a87cb-934">Den här tjänsten avslutar en TLS-session som representeras av en NX_SECURE_TLS_SESSION-struktur instans genom att skicka TLS CloseNotify-meddelandet till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-934">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="a87cb-935">Tjänsten väntar sedan på att fjärrvärden ska svara med sitt eget CloseNotify-meddelande.</span><span class="sxs-lookup"><span data-stu-id="a87cb-935">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="a87cb-936">Om fjärrvärden inte skickar ett CloseNotify-meddelande, betraktas TLS som ett fel och en möjlig säkerhets överträdelse, så det är viktigt att kontrol lera returvärdet för en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-936">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="a87cb-937">Parametern **wait_option** kan användas för att styra hur länge tjänsten ska vänta på svaret innan kontrollen återgår till anrops tråden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-937">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-938">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-938">Parameters</span></span>

- <span data-ttu-id="a87cb-939">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-939">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-940">**wait_option** Anger hur länge tjänsten ska vänta på svar från den fjärranslutna värden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-940">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-941">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-941">Return Values</span></span>

- <span data-ttu-id="a87cb-942">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-942">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-943">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) fick inget svar från fjärrvärden innan tids gränsen nåddes.</span><span class="sxs-lookup"><span data-stu-id="a87cb-943">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="a87cb-944">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0X111) kunde inte allokera ett paket för att skicka CloseNotify-meddelandet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-944">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="a87cb-945">**NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) kunde inte skicka CloseNotify-meddelandet via TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-945">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="a87cb-946">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-946">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-947">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-947">Allowed From</span></span>

<span data-ttu-id="a87cb-948">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-948">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-949">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-949">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-950">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-950">See Also</span></span>

- <span data-ttu-id="a87cb-951">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-951">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-952">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-952">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-953">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-953">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-954">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-954">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-955">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-955">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-956">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-956">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-957">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-957">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="a87cb-958">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-958">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="a87cb-959">Ställ in bufferten för paket ommontering för en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-959">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-960">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-960">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="a87cb-961">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-961">Description</span></span>

<span data-ttu-id="a87cb-962">Den här tjänsten associerar en paket omassembly-buffert till en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-962">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="a87cb-963">För att dekryptera och tolka inkommande TLS-poster måste data i varje post monteras från de underliggande TCP-paketen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-963">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="a87cb-964">TLS-poster kan vara upp till 16 KB i storlek (även om de ofta är mycket mindre) så att de inte får plats i ett enda TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="a87cb-964">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="a87cb-965">Om du vet att det inkommande meddelandets storlek är mindre än TLS-postgränsen på 16 KB kan buffertstorleken bli mindre, men för att hantera okända inkommande data måste bufferten göras så stor som möjligt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-965">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="a87cb-966">Om en inkommande post är större än den angivna bufferten avslutas TLS-sessionen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-966">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-967">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-967">Parameters</span></span>

- <span data-ttu-id="a87cb-968">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-968">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-969">**buffer_ptr** Pekare för att buffra för TLS som ska användas för paket ommontering.</span><span class="sxs-lookup"><span data-stu-id="a87cb-969">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="a87cb-970">**buffer_size** Storlek på angiven buffert i byte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-970">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-971">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-971">Return Values</span></span>

- <span data-ttu-id="a87cb-972">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-972">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-973">**NX_INVALID_PARAMETERS** (0X4D) ogiltig buffert eller TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-973">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-974">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-974">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-975">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-975">Allowed From</span></span>

<span data-ttu-id="a87cb-976">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-976">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-977">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-977">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-978">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-978">See Also</span></span>

- <span data-ttu-id="a87cb-979">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-979">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-980">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-980">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-981">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-981">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-982">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-982">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-983">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-983">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-984">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-984">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-985">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-985">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="a87cb-986">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="a87cb-986">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="a87cb-987">Åsidosätt standard versionen av TLS-protokollet för en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-987">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-988">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-988">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="a87cb-989">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-989">Description</span></span>

<span data-ttu-id="a87cb-990">Den här tjänsten åsidosätter standard versionen (nyaste) TLS-protokollet som används av en viss session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-990">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="a87cb-991">Detta gör att NetX Secure TLS kan använda en äldre version av TLS för en speciell TLS-session utan att inaktivera nya TLS-versioner vid kompilering.</span><span class="sxs-lookup"><span data-stu-id="a87cb-991">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="a87cb-992">Detta kan vara användbart i program som kan behöva kommunicera med en äldre värd som inte stöder den senaste versionen av TLS.</span><span class="sxs-lookup"><span data-stu-id="a87cb-992">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-993">*Från och med version 5.11 SP3 stöder NetX Secure TLS RFC 7507 (se OBS! nedan) och alla åsidosättningar till en äldre version med detta API leder till att en återställnings SCSV skickas i sitt hälsnings. Om servern har stöd för en nyare version av TLS och återställnings SCSV ingår i sitt hälsnings, kommer servern att avbryta TLS-handskakningen med en "olämplig återställning"-avisering. SCSV skickas endast när den åsidosättande versionen är en äldre version av TLS än vad som är aktiverat (t. ex. om du åsidosätter versionen till TLS 1,2 kommer inga SCSV att skickas).*</span><span class="sxs-lookup"><span data-stu-id="a87cb-993">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="a87cb-994">Giltiga värden för parametern protocol_version är följande makron: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 och NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="a87cb-994">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="a87cb-995">Makron NX_SECURE_TLS_DISABLE_TLS_1_1 och NX_SECURE_TLS_ENABLE_TLS_1_0 kan användas för att kontrol lera vilka versioner av TLS som kompileras i programmet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-995">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="a87cb-996">TLS version 1,2 är alltid aktiverat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-996">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="a87cb-997">Observera att om fjärrvärden inte stöder den angivna versionen kommer anslutningen att Miss Miss läge – endast den angivna åsidosättning-versionen kommer att förhandlas av NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="a87cb-997">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-998">RFC 7507: TLS fallback SCSV.</span><span class="sxs-lookup"><span data-stu-id="a87cb-998">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="a87cb-999">Den här RFC introducerades för att minimera ett säkerhets problem som ursprungligen orsakades av servrar som felaktigt hanterade protokoll nedgradering, och som i stället avvisade andra giltiga sitt hälsnings-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-999">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="a87cb-1000">I ett försök att fortsätta att vara kompatibelt med dessa gamla servrar startade vissa TLS-klientprogram att nya försök misslyckades med och äldre TLS-version (t. ex. TLS 1,2 misslyckades, så testa TLS 1,1).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1000">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="a87cb-1001">Den här lösningen introducerade dock ett nytt problem – en angripare kan tvinga en klient att nedgradera genom att artificiellt introducera ett nätverks-eller paket fel som orsakar att Server anslutningen kraschar – även om den nya TLS-versionen stöds av servern.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1001">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="a87cb-1002">Genom att nedgradera till en äldre version kan angriparen utnyttja svagheter i den versionen (SSLv3<sup>21</sup> är särskilt beroende av Poodle-attacken).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1002">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="a87cb-1003">För att förhindra den här situationen är RFC 7507 introdued "fallback SCSV", en pseudo-ciphersuite<sup>22</sup> som skickas i sitt hälsnings som meddelar en TLS-server när en TLS-klient använder en TLS-version som inte stöds av den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1003">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="a87cb-1004">På så sätt kan en server som har stöd för en nyare version avvisa en sitt hälsnings som innehåller återställnings-SCSV och förhindra nedgradering av angrepp.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1004">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="a87cb-1005">NetX Secure implementerar inte SSLv3 på grund av kända allvarliga svagheter som POODLE.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1005">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="a87cb-1006">Ett pseudo-ciphersuite-eller SCSV-värde (Signaling cipher Suite) är ett reserverat ciphersuite-nummer som används för att signalera aktiverade TLS-implementeringar om funktioner som inte är tillgängliga i äldre TLS-versioner.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1006">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="a87cb-1007">Återställnings SCSV och TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) är exempel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1007">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1008">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1008">Parameters</span></span>

- <span data-ttu-id="a87cb-1009">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1009">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1010">**protocol_version** TLS-version makro för den angivna TLS-versionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1010">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1011">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1011">Return Values</span></span>

- <span data-ttu-id="a87cb-1012">**NX_SUCCESS** (0x00) status ändring har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1012">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="a87cb-1013">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1013">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-1014">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) känd men TLS-version som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1014">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="a87cb-1015">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ogiltig protokoll version.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1015">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1016">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1016">Allowed From</span></span>

<span data-ttu-id="a87cb-1017">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1017">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1018">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1018">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1019">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1019">See Also</span></span>

- <span data-ttu-id="a87cb-1020">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1020">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1021">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1021">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="a87cb-1022">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1022">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="a87cb-1023">Ta emot data från en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1023">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1024">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1024">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a87cb-1025">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1025">Description</span></span>

<span data-ttu-id="a87cb-1026">Den här tjänsten tar emot data från den angivna aktiva TLS-sessionen och hanterar Dekrypteringen av dessa data innan den tillhandahålls till anroparen i NX_PACKET-parametern.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1026">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="a87cb-1027">Om inga data har ställts i kö i den angivna sessionen pausas anropet baserat på det angivna wait-alternativet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1027">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-1028">*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1028">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1029">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1029">Parameters</span></span>

- <span data-ttu-id="a87cb-1030">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1030">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1031">**packet_ptr** Pekare till en tilldelad TLS-paket-pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1031">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="a87cb-1032">**wait_option** Anger hur länge tjänsten ska vänta på ett paket från den fjärranslutna värden innan den returneras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1032">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1033">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1033">Return Values</span></span>

- <span data-ttu-id="a87cb-1034">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1034">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-1035">**NX_NO_PACKET** (0X01) inga data togs emot.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1035">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="a87cb-1036">**NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1036">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="a87cb-1037">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett mottaget meddelande misslyckades med en hash-kontroll för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1037">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="a87cb-1038">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett mottaget meddelande innehöll en okänd protokoll version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1038">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="a87cb-1039">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) tog emot en TLS-avisering från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1039">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="a87cb-1040">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1040">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="a87cb-1041">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1041">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1042">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1042">Allowed From</span></span>

<span data-ttu-id="a87cb-1043">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1043">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1044">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1044">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1045">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1045">See Also</span></span>

- <span data-ttu-id="a87cb-1046">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1046">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="a87cb-1047">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1047">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1048">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1048">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1049">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1049">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1050">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-1050">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-1051">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-1051">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-1052">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-1052">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="a87cb-1053">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1053">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="a87cb-1054">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1054">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="a87cb-1055">Tilldela ett återanrop som ska anropas i början av en omförhandling av en session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1055">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1056">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1056">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="a87cb-1057">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1057">Description</span></span>

<span data-ttu-id="a87cb-1058">Den här tjänsten tilldelar en motringning till en TLS-session som ska anropas varje gång det första meddelandet i en handhandlings hand skakning tas emot från den fjärranslutna värden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1058">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="a87cb-1059">Motringningsfunktionen är avsedd som ett meddelande till programmet som en handhandlings hand skakning startar – programmet kan välja att avsluta TLS-sessionen genom att returnera ett värde som inte är noll från återanropet, vilket gör att TLS avslutar TLS-sessionen med ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1059">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="a87cb-1060">Om programmet vill fortsätta med omförhandlingen bör återanropet returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1060">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="a87cb-1061">*På grund av semantiken för TLS-omförhandling anropas återanropet för NetX-säkra TLS-klienter när en HelloRequest tas emot från fjärrservern, men inte när klienten initierar omförhandlingar. På NetX säkra TLS-servrar anropas återanropet varje gång en sitt hälsnings tas emot (alla sitt hälsnings som tas emot i kontexten för en aktiv TLS-session). Det innebär att återanropet anropas om fjärrvärden eller det lokala programmet har initierat omförhandlingaret eftersom TLS-servern skickar en HelloRequest som fjärrklienten svarar på.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1061">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="a87cb-1062">NetX Secure TLS implementerar tillägget för säker omförhandling inidication från RFC 5746 för att säkerställa att hand skaknings hand skakningar inte omfattas av man-in-the-middle-attacker.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1062">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1063">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1063">Parameters</span></span>

- <span data-ttu-id="a87cb-1064">**session_ptr** Pekare till instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1064">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1065">**func_ptr** Pekare till callback-funktion.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1065">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1066">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1066">Return Values</span></span>

- <span data-ttu-id="a87cb-1067">**NX_SUCCESS** (0x00) återanrops tilldelningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1067">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="a87cb-1068">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare för callback-funktionen eller TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1068">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1069">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1069">Allowed From</span></span>

<span data-ttu-id="a87cb-1070">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1070">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1071">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1071">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1072">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1072">See Also</span></span>

- <span data-ttu-id="a87cb-1073">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1073">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1074">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1074">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1075">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1075">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-1076">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-1076">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-1077">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1077">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="a87cb-1078">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1078">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="a87cb-1079">Starta en handhandlings hand skakning med fjärrvärden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1079">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1080">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1080">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a87cb-1081">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1081">Description</span></span>

<span data-ttu-id="a87cb-1082">Den här tjänsten initierar en *handhandlings* hand skakning med en ansluten fjärran SLUTen TLS-värd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1082">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="a87cb-1083">En omförhandling består av en andra TLS-handskakning inom kontexten för en tidigare upprättad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1083">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="a87cb-1084">Var och en av de nya hand skaknings meddelandena krypteras med TLS-sessionen tills nya sessionsnycklar skapas och ChangeCipherSpec-meddelanden byts ut, då de nya nycklarna används för att kryptera alla meddelanden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1084">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="a87cb-1085">En omförhandling kan initieras när som helst när en TLS-session har upprättats.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1085">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="a87cb-1086">Om det görs ett försök till en omförhandling vid en TLS-handskakning eller innan en TLS-session upprättas utförs ingen åtgärd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1086">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="a87cb-1087">*En hel TLS-handskakning kommer att utföras när den här tjänsten anropas så att statusen slutförd och returnerad status varierar beroende på de aktuella TLS-inställningarna och session parametrarna.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1087">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="a87cb-1088">NetX Secure TLS implementerar tillägget för säker omförhandling inidication från RFC 5746 för att säkerställa att hand skaknings hand skakningar inte omfattas av man-in-the-middle-attacker.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1088">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1089">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1089">Parameters</span></span>

- <span data-ttu-id="a87cb-1090">**session_ptr** Pekare till instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1090">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1091">**wait_option** Anger hur länge tjänsten ska vänta på ett paket från den fjärranslutna värden innan den returneras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1091">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="a87cb-1092">Detta skickas till alla NetX-tjänster i TLS.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1092">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1093">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1093">Return Values</span></span>

- <span data-ttu-id="a87cb-1094">**NX_SUCCESS** (0x00) omförhandlingar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1094">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="a87cb-1095">**NX_NO_PACKET** (0X01) inga data togs emot.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1095">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="a87cb-1096">**NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1096">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="a87cb-1097">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett mottaget meddelande misslyckades med en hash-kontroll för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1097">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="a87cb-1098">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett mottaget meddelande innehöll en okänd protokoll version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1098">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="a87cb-1099">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) tog emot en TLS-avisering från fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1099">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="a87cb-1100">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0X134) den lokala eller fjärranslutna TLS-sessionen är inaktiv, vilket gör det omöjligt att göra en omförhandling.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1100">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="a87cb-1101">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) angavs inte fjärrvärden antingen SCSV eller säkert omförhandlat tillägg och därför kan omförhandla inte utföras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1101">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="a87cb-1102">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1102">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="a87cb-1103">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1103">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="a87cb-1104">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) den underliggande paket tilldelningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1104">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1105">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1105">Allowed From</span></span>

<span data-ttu-id="a87cb-1106">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1106">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1107">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1107">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1108">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1108">See Also</span></span>

- <span data-ttu-id="a87cb-1109">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1109">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1110">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1110">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1111">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1111">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-1112">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-1112">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-1113">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1113">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="a87cb-1114">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="a87cb-1114">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="a87cb-1115">Ta bort och Återställ en NetX säker TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1115">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1116">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1116">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-1117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1117">Description</span></span>

<span data-ttu-id="a87cb-1118">Den här tjänsten rensar en TLS-session och återställer statusen som om sessionen hade skapats så att ett befintligt TLS-sessionsobjekt kan återanvändas för en ny session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1118">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1119">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1119">Parameters</span></span>

- <span data-ttu-id="a87cb-1120">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1120">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1121">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1121">Return Values</span></span>

- <span data-ttu-id="a87cb-1122">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1122">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-1123">**NX_INVALID_PARAMETERS** (0X4D) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1123">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-1124">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1124">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1125">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1125">Allowed From</span></span>

<span data-ttu-id="a87cb-1126">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1126">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1127">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1127">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1128">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1128">See Also</span></span>

- <span data-ttu-id="a87cb-1129">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1129">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1130">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1130">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1131">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1131">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1132">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-1132">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-1133">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-1133">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-1134">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1134">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-1135">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1135">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="a87cb-1136">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-1136">nx_secure_tls_session_send</span></span>

<span data-ttu-id="a87cb-1137">Skicka data via en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1137">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1138">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1138">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a87cb-1139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1139">Description</span></span>

<span data-ttu-id="a87cb-1140">Den här tjänsten skickar data i den angivna NX_PACKET, använder den angivna aktiva TLS-sessionen och hanterar krypteringen av dessa data innan den skickas till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1140">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="a87cb-1141">Om mottagarens senaste annonserade fönster storlek är mindre än den här begäran, pausas tjänsten, om det finns ett alternativ för den angivna vänte tiden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1141">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-1142">*Om ett fel returneras ska programmet inte släppa paketet efter det här anropet. På så sätt kan oväntade resultat uppstå, eftersom nätverks driv rutinen kommer att släppa paketet efter överföringen.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1142">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1143">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1143">Parameters</span></span>

- <span data-ttu-id="a87cb-1144">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1144">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1145">**packet_ptr** Pekar på ett TLS-paket som innehåller data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1145">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="a87cb-1146">**wait_option** Definierar hur tjänsten fungerar om begäran är större än mottagarens fönster storlek.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1146">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1147">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1147">Return Values</span></span>

- <span data-ttu-id="a87cb-1148">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1148">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-1149">**NX_NO_PACKET** (0X01) inga data togs emot.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1149">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="a87cb-1150">**NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1150">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="a87cb-1151">**NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) den underliggande TCP-socketen kunde inte skickas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1151">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="a87cb-1152">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1152">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="a87cb-1153">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1153">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1154">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1154">Allowed From</span></span>

<span data-ttu-id="a87cb-1155">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1156">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1156">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1157">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1157">See Also</span></span>

- <span data-ttu-id="a87cb-1158">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1158">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="a87cb-1159">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1159">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1160">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1160">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1161">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1161">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="a87cb-1162">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1162">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1163">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-1163">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-1164">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1164">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-1165">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-1165">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="a87cb-1166">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1166">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="a87cb-1167">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1167">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="a87cb-1168">Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-servers hand skakning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1168">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1169">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1169">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="a87cb-1170">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1170">Description</span></span>

<span data-ttu-id="a87cb-1171">Den här tjänsten tilldelar en funktion pekare till en TLS-session som TLS kommer att anropa när en TLS-servers hand skakning har tagit emot ett sitt hälsnings-meddelande.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1171">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="a87cb-1172">Funktionen motringning gör att ett program kan bearbeta alla TLS-tillägg från det mottagna sitt hälsnings-meddelandet som kräver indatamängds-eller besluts fattande.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1172">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="a87cb-1173">Återanropet körs med inaktive ring av TLS-sessionens kontroll block och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1173">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="a87cb-1174">Matrisen med tilläggs objekt är avsedd att skickas till en hjälp funktion som söker efter och tolkar ett särskilt tillägg.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1174">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="a87cb-1175">En exempel hjälp funktion som analyserar TLS-tillägg som finns i Hello-meddelanden finns *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1175">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="a87cb-1176">Server återanrop kan också användas för att välja det aktiva identitets certifikatet med hjälp av *nx_secure_tls_active_certificate_set* för TLS-servern.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1176">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="a87cb-1177">Detta inträffar ofta som svar på ett Servernamnindikator-tillägg (SNI), vilket gör att en TLS-klient kan ange vilken server som försöker kontaktas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1177">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="a87cb-1178">Mer information finns i referenserna för *nx_secure_tls_session_sni_extension_parse* och *nx_secure_tls_active_certificate_set* .</span><span class="sxs-lookup"><span data-stu-id="a87cb-1178">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1179">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1179">Parameters</span></span>

- <span data-ttu-id="a87cb-1180">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1180">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1181">**func_ptr** Pekar till funktionen motringning för TLS-server.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1181">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1182">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1182">Return Values</span></span>

- <span data-ttu-id="a87cb-1183">**NX_SUCCESS** (0x00) allokering av funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1183">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="a87cb-1184">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1184">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1185">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1185">Allowed From</span></span>

<span data-ttu-id="a87cb-1186">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1186">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1187">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1187">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1188">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1188">See Also</span></span>

- <span data-ttu-id="a87cb-1189">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1189">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1190">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1190">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="a87cb-1191">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1191">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="a87cb-1192">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1192">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="a87cb-1193">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-1193">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="a87cb-1194">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-1194">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="a87cb-1195">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1195">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="a87cb-1196">Parsa ett Servernamnindikator-tillägg (SNI) som tagits emot från en TLS-klient</span><span class="sxs-lookup"><span data-stu-id="a87cb-1196">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1197">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1197">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="a87cb-1198">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1198">Description</span></span>

<span data-ttu-id="a87cb-1199">Den här tjänsten är avsedd att anropas inifrån en motringning till en TLS-server som har lagts till i en TLS-session med hjälp av nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1199">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="a87cb-1200">Återanropet anropas när ett sitt hälsnings-meddelande togs emot från en fjärran sluten TLS-klient och anges en matris med tillgängliga tillägg (och antalet tillägg i matrisen).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1200">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="a87cb-1201">Matrisen och dess längd kan skickas direkt till den här rutinen för att avgöra om det finns ett SNI-tillägg, annars returneras NX_SECURE_TLS_EXTENSION_NOT_FOUND som anger att klienten inte valde att Provice SNI-tillägget (detta är inte ett fel).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1201">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="a87cb-1202">Om SNI-tillägget hittas returneras X. 509 DNS-namnet som anges av TLS-klienten i dns_names strukturen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1202">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="a87cb-1203">För närvarande tillhandahåller SNI-tillägget endast en enda DNS-namns post som kan användas av TLS-servern för att avgöra vilket identitets certifikat som ska skickas till fjärrklienten. \* \*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1203">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="a87cb-1204">NX_SECURE_X509_DNS_NAME strukturen innehåller bara DNS-namnet som en UCHAR-sträng i fältet *nx_secure_x509_dns_name* och längden på namn strängen i *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1204">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="a87cb-1205">Makro NX_SECURE_X509_DNS_NAME_MAX kontrollerar storleken på nx_secure_x509_dns_name bufferten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1205">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1206">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1206">Parameters</span></span>

- <span data-ttu-id="a87cb-1207">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1207">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1208">**tillägg** Pekar mot en matris med TLS Hello-tillägg (från motringning till session).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1208">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="a87cb-1209">**num_extensions** Antal tillägg i matrisen (från motringning till session).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1209">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="a87cb-1210">**dns_name** Returnera DNS-namnet som anges i SNI-tillägget.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1210">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1211">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1211">Return Values</span></span>

- <span data-ttu-id="a87cb-1212">**NX_SUCCESS** (0x00) parsning av tillägget har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1212">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="a87cb-1213">**NX_PTR_ERROR** (0X07) ogiltig tillägg mat ris eller TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1213">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-1214">Det gick inte att hitta **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0X136) SNI-tillägget.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1214">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="a87cb-1215">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0X137) SNI Extension-formatet var ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1215">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1216">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1216">Allowed From</span></span>

<span data-ttu-id="a87cb-1217">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1218">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1218">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="a87cb-1219">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1219">See Also</span></span>

- <span data-ttu-id="a87cb-1220">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1220">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="a87cb-1221">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1221">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="a87cb-1222">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1222">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="a87cb-1223">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1223">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="a87cb-1224">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1224">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="a87cb-1225">Ange ett Servernamnindikator-tillägg (SNI) som ska skickas till en fjärrserver</span><span class="sxs-lookup"><span data-stu-id="a87cb-1225">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1226">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1226">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="a87cb-1227">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1227">Description</span></span>

<span data-ttu-id="a87cb-1228">Med den här tjänsten kan ett TLS-klientcertifikat tillhandahålla ett DNS-namn för önskad server till en fjärr-TLS-server med hjälp av tillägget Servernamnindikator (SNI) TLS.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1228">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="a87cb-1229">SNI-tillägget gör att servern kan välja rätt identitets certifikat och parametrar baserat på klientens angivna Server inställningar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1229">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="a87cb-1230">SNI-tillägget har för närvarande endast stöd för ett enda DNS-namn som ska skickas, och därför parametern för singular Name.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1230">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="a87cb-1231">Parametern dns_name måste initieras med *nx_secure_x509_dns_name_initialize* och kommer att innehålla klientens primära server.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1231">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="a87cb-1232">Om du vill ta bort tilläggets namn, anropar du bara den här tjänsten med parametervärdet "dns_name" för NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1232">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="a87cb-1233">NX_SECURE_X509_DNS_NAME strukturen innehåller bara DNS-namnet som en UCHAR-sträng i fältet  *nx_secure_x509_dns_name* och längden på namn strängen i *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1233">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="a87cb-1234">Makro NX_SECURE_X509_DNS_NAME_MAX kontrollerar storleken på nx_secure_x509_dns_name bufferten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1234">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="a87cb-1235">*Den här rutinen måste anropas innan nx_secure_tls_session_start anropas eller så innehåller sitt hälsnings inte SNI-tillägget.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1235">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1236">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1236">Parameters</span></span>

- <span data-ttu-id="a87cb-1237">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1237">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1238">**dns_name** DNS-namnet som angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1238">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1239">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1239">Return Values</span></span>

- <span data-ttu-id="a87cb-1240">**NX_SUCCESS** (0x00) tillägget av DNS-servernamnet är klart.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1240">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="a87cb-1241">**NX_PTR_ERROR** (0X07) ogiltigt DNS-namn eller en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1241">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1242">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1242">Allowed From</span></span>

<span data-ttu-id="a87cb-1243">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1243">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1244">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1244">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1245">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1245">See Also</span></span>

- <span data-ttu-id="a87cb-1246">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1246">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1247">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1247">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="a87cb-1248">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1248">nx_secure_tls_session_start</span></span>

<span data-ttu-id="a87cb-1249">Starta en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1249">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1250">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1250">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a87cb-1251">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1251">Description</span></span>

<span data-ttu-id="a87cb-1252">Den här tjänsten startar en TLS-session med det angivna TLS-sessionens kontroll block och en ansluten TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1252">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="a87cb-1253">TCP-anslutningen måste redan ha slutförts efter ett lyckat anrop till antingen nx_tcp_client_socket_connect eller nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1253">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="a87cb-1254">Den här tjänsten avgör typen av TLS-session (klient eller server) från TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1254">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="a87cb-1255">Alternativet wait definierar hur tjänsten fungerar medan TLS-handskakningen pågår.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1255">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1256">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1256">Parameters</span></span>

- <span data-ttu-id="a87cb-1257">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1257">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1258">**tcp_socket_ptr** Pekar till en ansluten TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1258">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="a87cb-1259">**wait_option** Definierar hur tjänsten fungerar medan TLS-handskakningen pågår.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1259">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1260">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1260">Return Values</span></span>

- <span data-ttu-id="a87cb-1261">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1261">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-1262">**NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1262">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="a87cb-1263">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) en mottagen TLS-meddelande typ är felaktig.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1263">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="a87cb-1264">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) ett chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1264">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="a87cb-1265">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Det gick inte att bearbeta meddelande bearbetningen under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1265">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="a87cb-1266">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett inkommande meddelande misslyckades med en hash Mac-kontroll.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1266">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="a87cb-1267">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka en underliggande TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1267">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="a87cb-1268">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) ett inkommande meddelande hade ett ogiltigt längd fält.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1268">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="a87cb-1269">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) ett inkommande ChangeCipherSpec-meddelande var felaktigt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1269">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="a87cb-1270">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0X10C) ett inkommande TLS-certifikat kan inte användas för att identifiera fjärr-TLS-servern.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1270">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="a87cb-1271">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0X10D) den offentliga nyckel chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1271">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="a87cb-1272">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) fjärrvärden har angett Inga krypteringssviter som stöds av netx Secure TLS-stacken.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1272">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="a87cb-1273">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett MOTTAGet TLS-meddelande hade en okänd TLS-version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1273">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="a87cb-1274">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) ett MOTTAGet TLS-meddelande hade en känd men TLS-version som inte stöds i huvudet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1274">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="a87cb-1275">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att tilldela en intern TLS-paket.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1275">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="a87cb-1276">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) fjärrvärden tillhandahöll ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1276">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="a87cb-1277">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) den fjärranslutna värden skickade en avisering som indikerar ett fel och att TLS-sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1277">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="a87cb-1278">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0X13B) en post i ciphersuite-tabellen hade en funktion pekare till null.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1278">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="a87cb-1279">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0X146) en fjärr-TLS-sitt hälsnings inkluderade reserv SCSV andattempted en versions återställning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1279">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="a87cb-1280">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1280">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1281">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1281">Allowed From</span></span>

<span data-ttu-id="a87cb-1282">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1283">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1283">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1284">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1284">See Also</span></span>

- <span data-ttu-id="a87cb-1285">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1285">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="a87cb-1286">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1286">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1287">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1287">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1288">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="a87cb-1288">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="a87cb-1289">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-1289">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-1290">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1290">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-1291">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1291">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="a87cb-1292">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="a87cb-1292">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="a87cb-1293">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1293">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1294">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="a87cb-1294">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="a87cb-1295">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="a87cb-1295">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="a87cb-1296">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="a87cb-1296">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="a87cb-1297">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="a87cb-1297">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="a87cb-1298">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="a87cb-1298">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="a87cb-1299">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-1299">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="a87cb-1300">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1300">nx_packet_allocate</span></span>
- <span data-ttu-id="a87cb-1301">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="a87cb-1301">nx_packet_data_append</span></span>
- <span data-ttu-id="a87cb-1302">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="a87cb-1302">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="a87cb-1303">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1303">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="a87cb-1304">Tilldela en timestamp-funktion till en NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1304">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1305">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1305">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="a87cb-1306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1306">Description</span></span>

<span data-ttu-id="a87cb-1307">Den här funktionen ställer in en funktions pekare som TLS anropar när den måste hämta den aktuella tiden, som används i olika TLS-handskaknings meddelanden och för att verifiera certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1307">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="a87cb-1308">Funktionen förväntas returnera aktuellt GMT i UNIX 32-bitars format (sekunder sedan den 1 januari 1970, UTC, som ignorerar skottår) enligt sitt hälsnings-kraven i TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1308">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="a87cb-1309">Om ingen tidsstämpel-funktion har tilldelats används värdet 0 för tidsstämpeln i TLS-handskakningen och kontroll av certifikatets giltighets tid fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1309">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1310">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1310">Parameters</span></span>

- <span data-ttu-id="a87cb-1311">**session_ptr** Pekare till en instans av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1311">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1312">**time_func_ptr** Pekar till en funktion som returnerar aktuell tid (GMT) i UNIX 32-bitars format.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1312">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1313">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1313">Return Values</span></span>

- <span data-ttu-id="a87cb-1314">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1314">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a87cb-1315">**NX_INVALID_PARAMETERS** (0X4D) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1315">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-1316">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1316">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1317">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1317">Allowed From</span></span>

<span data-ttu-id="a87cb-1318">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1318">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1319">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1319">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1320">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1320">See Also</span></span>

- <span data-ttu-id="a87cb-1321">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1321">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1322">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1322">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1323">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="a87cb-1323">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="a87cb-1324">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="a87cb-1324">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="a87cb-1325">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="a87cb-1325">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="a87cb-1326">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1326">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="a87cb-1327">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-1327">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="a87cb-1328">Lägg till betrott certifikat i NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1328">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1329">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1329">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="a87cb-1330">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1330">Description</span></span>

<span data-ttu-id="a87cb-1331">Den här tjänsten lägger till en initierad NX_SECURE_X509_CERT struktur instans till en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1331">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="a87cb-1332">Det här certifikatet används av TLS-stacken för att verifiera certifikat som tillhandahålls av fjärrvärden under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1332">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="a87cb-1333">Betrodda certifikat krävs för TLS-klient läge.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1333">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="a87cb-1334">Betrodda certifikat krävs bara för TLS server-läge om autentisering av klient certifikat är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1334">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1335">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1335">Parameters</span></span>

- <span data-ttu-id="a87cb-1336">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1336">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1337">**certificate_ptr** Pekar mot en initierad TLS-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1337">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1338">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1338">Return Values</span></span>

- <span data-ttu-id="a87cb-1339">**NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1339">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="a87cb-1340">**NX_INVALID_PARAMETERS** (0X4D) försökte lägga till ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1340">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="a87cb-1341">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1341">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1342">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1342">Allowed From</span></span>

<span data-ttu-id="a87cb-1343">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1343">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1344">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1344">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1345">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1345">See Also</span></span>

- <span data-ttu-id="a87cb-1346">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1346">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1347">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1347">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1348">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1348">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1349">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-1349">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="a87cb-1350">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="a87cb-1350">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="a87cb-1351">Ta bort betrott certifikat från NetX Secure TLS-session</span><span class="sxs-lookup"><span data-stu-id="a87cb-1351">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1352">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1352">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="a87cb-1353">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1353">Description</span></span>

<span data-ttu-id="a87cb-1354">Den här tjänsten tar bort ett betrott certifikat från en TLS-session, som anges i fältet eget namn i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1354">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1355">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1355">Parameters</span></span>

- <span data-ttu-id="a87cb-1356">**session_ptr** Pekare till en tidigare skapad TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1356">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="a87cb-1357">**common_name** Värdet för eget namn för det certifikat som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1357">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="a87cb-1358">**common_name_length** Längden på den gemensamma namn strängen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1358">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1359">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1359">Return Values</span></span>

- <span data-ttu-id="a87cb-1360">**NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1360">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="a87cb-1361">**NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1361">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="a87cb-1362">Det gick inte att hitta **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** -certifikat (0x119).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1362">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1363">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1363">Allowed From</span></span>

<span data-ttu-id="a87cb-1364">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1364">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1365">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1365">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1366">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1366">See Also</span></span>

- <span data-ttu-id="a87cb-1367">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1367">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="a87cb-1368">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1368">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1369">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1369">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1370">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-1370">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="a87cb-1371">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1371">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="a87cb-1372">Initiera X. 509-certifikat för NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="a87cb-1372">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1373">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1373">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a87cb-1374">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1374">Description</span></span>

<span data-ttu-id="a87cb-1375">Den här tjänsten initierar en NX_SECURE_X509_CERT-struktur från ett binärt kodat X. 509-certifikat för användning i en TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1375">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="a87cb-1376">Certifikat data **måste** vara ett giltigt X. 509-digitalt certifikat i der-kodat binärt format.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1376">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="a87cb-1377">Datan kan vara en del av vilken källa som helst (t. ex. fil system, kompilerad konstant buffert osv.) så länge en UCHAR pekar på dessa data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1377">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="a87cb-1378">Parametern *raw_data_buffer* och dess storlek är valfria parametrar som anger en dedikerad buffert som certifikat data kopieras till före parsning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1378">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="a87cb-1379">Om raw_data_buffer skickas som NX_NULL kommer NX_SECURE_X509_CERTs strukturen att peka direkt i certificate_data matrisen (buffer_size ignoreras i det här fallet).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1379">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="a87cb-1380">Om raw_data_buffer skickas som NX_NULL ska du ***inte*** ändra de data som pekar på certificate_data pekare eller certifikat bearbetningen kommer troligen att Miss lyckat!</span><span class="sxs-lookup"><span data-stu-id="a87cb-1380">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="a87cb-1381">Den privata nyckel parametern är för lokala identitets certifikat – den privata nyckeln används av servrar för att dekryptera inkommande nyckel data från en klient (krypterad med serverns offentliga nyckel) och av klienter för att verifiera sin identitet på en server när servern begär ett klient certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1381">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="a87cb-1382">Om du lägger till en privat nyckel med det här API: et så markeras automatiskt det associerade certifikatet som ett identitets certifikat för ett TLS-program.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1382">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="a87cb-1383">Vid initiering av certifikat för andra syfte (t. ex. det betrodda arkivet) ska parametern *private_key_data* skickas som NULL, *private_key_data_length* som 0 och *private_key_type* ska skickas som NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1383">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="a87cb-1384">Parametern *private_key_type* anger formateringen för den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1384">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="a87cb-1385">Om den privata nyckeln till exempel är en DER-kodad PKCS # 1-format-RSA-nyckel, ska private_key_type skickas som NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, en typ som är känd för att tolkas omedelbart och sparas för senare användning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1385">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="a87cb-1386">Private_key_type har även stöd för användardefinierade nyckel typer<sup>23</sup> för plattformar och program som har vissa nyckel format eller andra behov.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1386">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="a87cb-1387">En maskinvarubaserad krypterings motor kan till exempel använda ett speciellt format som inte kan tolkas av NetX-säkra program, eller så kan en privat nyckel krypteras eller representeras av en kryptografisk token som kan vara fallet med en Trusted Platform Module (TPM) eller PKCS # 11-kryptografisk maskin vara.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1387">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="a87cb-1388">När en användardefinierad nyckel typ används skickas nyckel data till orda Grant till lämplig kryptografisk rutin – till exempel skulle en privat RSA-nyckel skickas, utan någon parsning eller bearbetning, direkt till den RSA-kryptografiska rutinen som tillhandahålls TLS i tabellen ciphersuite.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1388">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="a87cb-1389">Den användardefinierade nyckel typen skickas också till den kryptografiska rutinen (vad gäller RSA, detta är "OP"-parametern).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1389">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="a87cb-1390">Intervallet för användardefinierade nycklar täcker den övre halvan av ett 32-bitars heltal utan tecken från 0x0001 0000-0xFFFF FFFF.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1390">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="a87cb-1391">Värden som är mindre än 0x0001 0000 är reserverade för NetX-säker användning.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1391">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="a87cb-1392">Användardefinierade nyckel typer är en avancerad funktion som kräver anpassade kryptografiska rutiner för att hantera rå data för den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1392">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="a87cb-1393">Kontakta din Express Logic-representant om du behöver den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1393">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1394">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1394">Parameters</span></span>

- <span data-ttu-id="a87cb-1395">**certificate_ptr** Pekar mot en oinitierad X. 509-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1395">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="a87cb-1396">**certificate_data** Pekare till DER-kodade X. 509 binära data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1396">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="a87cb-1397">**raw_data_buffer** Pekare till valfri dedikerad certifikat data buffert.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1397">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="a87cb-1398">**buffer_size** Storlek på valfri dedikerad certifikat data buffert.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1398">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="a87cb-1399">**certificate_data_length** Längden på certifikatets binära data i byte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1399">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="a87cb-1400">**private_key_data** Pekare till valfria privata nyckel data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1400">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="a87cb-1401">**private_key_data_length** Längd på data för privata nycklar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1401">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="a87cb-1402">**private_key_type** Nyckel typs identifierare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1402">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1403">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1403">Return Values</span></span>

- <span data-ttu-id="a87cb-1404">**NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1404">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="a87cb-1405">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1405">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="a87cb-1406">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0X112) certifikat data innehöll inte något der-kodat X. 509-certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1406">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="a87cb-1407">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** -certifikatet (0x10D) saknar ett offentligt nyckels chiffer som stöds av netx Secure.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1407">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="a87cb-1408">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0X186) privat nyckel eller certifikat innehåller ingen giltig ASN. 1-sekvens.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1408">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="a87cb-1409">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0X18A) den angivna privata nyckeln var inte en giltig PKCS # 1 RSA-nyckel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1409">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="a87cb-1410">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0X19D) den angivna privata nyckel typen var inte användardefinierad och matchade inte någon känd typ.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1410">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1411">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1411">Allowed From</span></span>

<span data-ttu-id="a87cb-1412">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1413">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1413">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1414">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1414">See Also</span></span>

- <span data-ttu-id="a87cb-1415">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="a87cb-1415">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="a87cb-1416">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1416">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1417">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="a87cb-1417">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="a87cb-1418">Importerar X. 509-certifikat till NetX Secure i kapitel 3.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1418">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="a87cb-1419">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1419">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="a87cb-1420">Kontrol lera DNS-namn mot X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-1420">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1421">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1421">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="a87cb-1422">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1422">Description</span></span>

<span data-ttu-id="a87cb-1423">Den här tjänsten kontrollerar ett certifikats nätverks namn mot ett topp domän namn (topp domän namn) som anroparen tillhandahåller för DNS-validering av en fjärrvärd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1423">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="a87cb-1424">Den här verktygs funktionen är avsedd att anropas inifrån en rutin för återanrop från certifikat validering som tillhandahålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1424">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="a87cb-1425">Namn på TOPPnivå ska vara den övre delen av den URL som används för att komma åt fjärrvärden ("." -separerad sträng före det första snedstrecket.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1425">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="a87cb-1426">Om det egna namnet innehåller ett jokertecken (till exempel *. example.com) matchar jokertecknet alla med samma suffix. Observera att endast det första jokertecknet (*"") som påträffas (läsning från höger till vänster) kommer att beaktas för matchning av jokertecken, till exempel ABC. \*. example. com matchar *alla* namn som slutar på ". example.com".</span><span class="sxs-lookup"><span data-stu-id="a87cb-1426">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="a87cb-1427">Om det egna namnet inte matchar den angivna strängen, parsas "subjectAltName"-tillägget (om det finns i certifikatet) och alla DNSName-poster också jämförs.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1427">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="a87cb-1428">Om ingen av dessa poster matchar returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1428">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="a87cb-1429">Det är viktigt att förstå formatet på det egna namnet (och subjectAltName-poster) i förväntade certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1429">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="a87cb-1430">Vissa certifikat kan till exempel använda en rå IP-adress eller ett jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1430">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="a87cb-1431">DNS-topp strängen måste vara formaterad så att den matchar de förväntade värdena i mottagna certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1431">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1432">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1432">Parameters</span></span>

- <span data-ttu-id="a87cb-1433">**certificate_ptr** Pekare till en X. 509-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1433">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="a87cb-1434">**dns_tld** Top-Level domän namn som ska jämföras med.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1434">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="a87cb-1435">**dns_tld_length** Längd på TOPPnivå sträng.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1435">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1436">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1436">Return Values</span></span>

- <span data-ttu-id="a87cb-1437">**NX_SUCCESS** (0x00) jämförelse med eget namn eller subjectAltName.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1437">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="a87cb-1438">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0X195) inget matchande namn hittades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1438">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="a87cb-1439">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1439">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1440">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1440">Allowed From</span></span>

<span data-ttu-id="a87cb-1441">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1442">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1442">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1443">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1443">See Also</span></span>

- <span data-ttu-id="a87cb-1444">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1444">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1445">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1445">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="a87cb-1446">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1446">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="a87cb-1447">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1447">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="a87cb-1448">Kontrol lera X. 509-certifikatet mot en angiven lista över återkallade certifikat (CRL)</span><span class="sxs-lookup"><span data-stu-id="a87cb-1448">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1449">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1449">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="a87cb-1450">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1450">Description</span></span>

<span data-ttu-id="a87cb-1451">Den här tjänsten tar en DER-kodad lista över återkallade certifikat och söker efter ett särskilt certifikat i listan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1451">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="a87cb-1452">Utfärdaren av listan över återkallade certifikat verifieras mot ett angivet certifikat arkiv. CRL-utfärdaren verifieras vara densamma som för det certifikat som kontrol leras och serie numret för det aktuella certifikatet används för att söka i listan över återkallade certifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1452">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="a87cb-1453">Om utfärdarna matchar kontrollerar signaturen och certifikatet **inte** finns i listan. anropet lyckas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1453">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="a87cb-1454">Alla andra fall orsakar att ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1454">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1455">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1455">Parameters</span></span>

- <span data-ttu-id="a87cb-1456">**crl_data** Pekare till en DER-kodad CRL.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1456">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="a87cb-1457">**crl_length** Längd i byte för CRL-data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1457">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="a87cb-1458">**lagra** Pekar på ett X. 509-certifikat arkiv.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1458">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="a87cb-1459">**certificate_ptr** Pekare till en X. 509-certifikat instans.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1459">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1460">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1460">Return Values</span></span>

- <span data-ttu-id="a87cb-1461">**NX_SUCCESS** (0x00) verifieringen av att certifikatet inte har återkallats.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1461">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="a87cb-1462">Det gick inte att hitta **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) för CRL-utfärdarcertifikat.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1462">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="a87cb-1463">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Det gick inte att hitta certifikatet för certifikat utfärdare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1463">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="a87cb-1464">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0X182) CRL ASN. 1 innehåller ett ogiltigt längd-fält.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1464">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="a87cb-1465">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG (0x189)** Listan över återkallade certifikat innehöll ogiltig ASN. 1.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1465">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="a87cb-1466">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Det gick inte att verifiera certifikat kedjan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1466">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="a87cb-1467">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0X197) CRL-och certifikat utfärdare matchade inte.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1467">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="a87cb-1468">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) signaturen för återkallade certifikat var ogiltig.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1468">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="a87cb-1469">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0X199) Det gick inte att hitta det certifikat som kontrol leras i CRL och därför återkallas.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1469">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="a87cb-1470">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1470">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1471">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1471">Allowed From</span></span>

<span data-ttu-id="a87cb-1472">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1473">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1473">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1474">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1474">See Also</span></span>

- <span data-ttu-id="a87cb-1475">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1475">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1476">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1476">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="a87cb-1477">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1477">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="a87cb-1478">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="a87cb-1478">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="a87cb-1479">Initiera en X. 509 DNS-namn struktur</span><span class="sxs-lookup"><span data-stu-id="a87cb-1479">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1480">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1480">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="a87cb-1481">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1481">Description</span></span>

<span data-ttu-id="a87cb-1482">Den här tjänsten initierar ett X. 509 DNS-namn för användning med vissa API-tjänster som kräver ett specifikt namn format.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1482">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="a87cb-1483">*Nx_secure_tls_sni_extension_parses* tjänsten förväntar sig till exempel ett NX_SECURE_X509_DNS_NAME-objekt för att matcha namnet som tillhandahålls av en fjärrvärd i servernamnindikator tillägget under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1483">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="a87cb-1484">Ett DNS-namn är helt enkelt en charater-sträng med en längd – den maximalt tillåtna längden på ett DNS-namn (och storleken på den interna bufferten i NX_SECURE_X509_DNS_NAME) styrs av makro NX_SECURE_X509_DNS_NAME_MAX (standard 100 byte).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1484">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1485">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1485">Parameters</span></span>

- <span data-ttu-id="a87cb-1486">**dns_name** DNS-namn strukturen att initiera.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1486">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="a87cb-1487">**name_string** DNS-namn sträng data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1487">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="a87cb-1488">**längd** Namn strängens längd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1488">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1489">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1489">Return Values</span></span>

- <span data-ttu-id="a87cb-1490">**NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1490">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="a87cb-1491">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0X19E) den tilldelade namn strängen överskred NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1491">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="a87cb-1492">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1492">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1493">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1493">Allowed From</span></span>

<span data-ttu-id="a87cb-1494">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1494">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1495">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1495">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="a87cb-1496">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1496">See Also</span></span>

- <span data-ttu-id="a87cb-1497">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="a87cb-1497">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="a87cb-1498">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1498">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="a87cb-1499">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1499">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="a87cb-1500">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1500">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="a87cb-1501">Hitta och parsa ett tillägg för utökad nyckel användning i X. 509 i ett X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-1501">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1502">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1502">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="a87cb-1503">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1503">Description</span></span>

<span data-ttu-id="a87cb-1504">Den här tjänsten är avsedd att anropas inifrån ett motanrop för certifikat verifiering (se *nx_secure_tls_session_certificate_callback_set)*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1504">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="a87cb-1505">Den söker efter ett angivet OID för utökad nyckel användning i ett X. 509-certifikat och returnerar om OID finns.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1505">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="a87cb-1506">Parametern key_usage är en heltals mappning av OID: er som används internt av NetX Secure X. 509 och TLS för att undvika att skicka OID-strängar med variabel längd som parametrar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1506">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="a87cb-1507">Relevanta OID för tillägget för utökad nyckel användning anges i tabellen nedan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1507">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="a87cb-1508">En typisk TLS-klientkonfiguration som vill kontrol lera den utökade nyckel användningen i ett mottaget TLS-servercertifikat skulle kunna söka efter förekomsten av OID-NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – om tillägget finns men att OID inte är det, skulle certifikatet anses vara ogiltigt för diskfel-värden som en TLS-server och återanropet av certifikat verifiering ska returnera ett fel.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1508">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="a87cb-1509">Om själva tillägget saknas är det upp till programmet om du vill fortsätta med TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1509">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="a87cb-1510">I återanropet av certifikat verifieringen är felet returkod NX_SECURE_X509_KEY_USAGE_ERROR reserverat för användning av program.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1510">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="a87cb-1511">Om det uppstår ett fel när nyckel användningen kontrol leras kan det här värdet returneras från återanropet för att indikera orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1511">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="a87cb-1512">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="a87cb-1512">NetX Secure Identifier</span></span>                                | <span data-ttu-id="a87cb-1513">OID-värde</span><span class="sxs-lookup"><span data-stu-id="a87cb-1513">OID Value</span></span>         | <span data-ttu-id="a87cb-1514">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1514">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="a87cb-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="a87cb-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="a87cb-1516">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="a87cb-1516">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="a87cb-1517">Certifikat kan användas för att identifiera en TLS-server</span><span class="sxs-lookup"><span data-stu-id="a87cb-1517">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="a87cb-1518">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="a87cb-1518">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="a87cb-1519">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="a87cb-1519">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="a87cb-1520">Certifikat kan användas för att identifiera en TLS-klient</span><span class="sxs-lookup"><span data-stu-id="a87cb-1520">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="a87cb-1521">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="a87cb-1521">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="a87cb-1522">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="a87cb-1522">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="a87cb-1523">Certifikat kan användas för att signera kod</span><span class="sxs-lookup"><span data-stu-id="a87cb-1523">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="a87cb-1524">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="a87cb-1524">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="a87cb-1525">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="a87cb-1525">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="a87cb-1526">Certifikat kan användas för att signera e-postmeddelanden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1526">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="a87cb-1527">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="a87cb-1527">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="a87cb-1528">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="a87cb-1528">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="a87cb-1529">Certifikat kan användas för att signera tidsstämplar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1529">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="a87cb-1530">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="a87cb-1530">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="a87cb-1531">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="a87cb-1531">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="a87cb-1532">Certifikat kan användas för att signera OCSP-svar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1532">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="a87cb-1533">OID och mappningar för tillägg för utökad nyckel användning i X. 509</span><span class="sxs-lookup"><span data-stu-id="a87cb-1533">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1534">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1534">Parameters</span></span>

- <span data-ttu-id="a87cb-1535">**certifikat** Pekare till certifikat som verifieras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1535">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="a87cb-1536">**key_usage** OID-heltals mappning från tabellen ovan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1536">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1537">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1537">Return Values</span></span>

- <span data-ttu-id="a87cb-1538">**NX_SUCCESS** (0X00) angiven OID för nyckel användning hittades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1538">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="a87cb-1539">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 kod för flera byte påträffades (certifikat som inte stöds).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1539">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="a87cb-1540">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) ett inidentifierat ASN. 1-fält påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1540">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1541">**NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) ogiltig ASN. 1-tagg klass påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1541">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1542">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0X192) ogiltigt tillägg påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1542">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1543">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0X19B) Det gick inte att hitta tillägget för utökad nyckel användning i det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1543">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="a87cb-1544">**NX_PTR_ERROR** (0X07) ogiltig certifikat pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1544">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1545">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1545">Allowed From</span></span>

<span data-ttu-id="a87cb-1546">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1546">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1547">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1547">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1548">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1548">See Also</span></span>

- <span data-ttu-id="a87cb-1549">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1549">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="a87cb-1550">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1550">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="a87cb-1551">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1551">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="a87cb-1552">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1552">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="a87cb-1553">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-1553">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="a87cb-1554">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-1554">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="a87cb-1555">Hitta och returnera ett X. 509-tillägg i ett X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-1555">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1556">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1556">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="a87cb-1557">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1557">Description</span></span>

<span data-ttu-id="a87cb-1558">Den här tjänsten är avsedd att anropas inifrån ett motanrop för certifikat verifiering (se *nx_secure_tls_session_certificate_callback_set)* och är en avancerad X. 509-tjänst.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1558">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="a87cb-1559">Funktionen söker efter ett särskilt tillägg i ett X. 509-certifikat baserat på en OID och returnerar om OID finns, tillsammans med en struktur som innehåller referenser till relevanta rå Extension-data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1559">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="a87cb-1560">Parametern extension_id är en heltals mappning av OID: er som används internt av NetX Secure X. 509 och TLS för att undvika att skicka OID-strängar med variabel längd som parametrar.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1560">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="a87cb-1561">Hjälp funktioner som tillhandahålls för vissa tillägg (till exempel *nx_secure_x509_key_usage_extension_parse*) anropa nx_secure_x509_extension_find internt för att hämta tilläggs data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1561">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="a87cb-1562">Relevanta OID för kända X. 509-tillägg anges i tabellen nedan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1562">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="a87cb-1563">NX_SECURE_X509_EXTENSION-strukturen innehåller pekare i X. 509-certifikatet som gör att hjälp funktioner som *nx_secure_x509_key_usage_extension_parse* snabbt kan avkoda de der-kodade ASN. 1-data som finns i RAW.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1563">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="a87cb-1564">Information om vissa tillägg finns i RFC 5280 (X. 509 Specification) eller referens för lämpliga hjälp funktioner om det är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1564">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="a87cb-1565">Den aktuella versionen av NetX Secure X. 509 har begränsat stöd för X. 509-tillägg.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1565">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="a87cb-1566">Fler hjälp funktioner kommer att läggas till i framtiden.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1566">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a87cb-1567">*Den här tjänsten är en avancerad funktion för användare som är bekanta med X. 509-tillägg och DER-kodat ASN. 1. Det ges möjlighet att ge dessa användare åtkomst till tillägg som NetX Secure X. 509 inte tillhandahåller hjälp funktioner för för närvarande. För dessa tillägg utan hjälp funktioner måste du själv parsa den råa DER-kodade ASN. 1.*</span><span class="sxs-lookup"><span data-stu-id="a87cb-1567">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="a87cb-1568">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="a87cb-1568">NetX Secure Identifier</span></span>                              | <span data-ttu-id="a87cb-1569">OID-värde</span><span class="sxs-lookup"><span data-stu-id="a87cb-1569">OID Value</span></span> | <span data-ttu-id="a87cb-1570">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1570">Description</span></span>                                                                    | <span data-ttu-id="a87cb-1571">Hjälp funktion?</span><span class="sxs-lookup"><span data-stu-id="a87cb-1571">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="a87cb-1572">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="a87cb-1572">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="a87cb-1573">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="a87cb-1573">2.5.29.9</span></span>  | <span data-ttu-id="a87cb-1574">Katalogattribut – grundläggande information om certifikat ämne</span><span class="sxs-lookup"><span data-stu-id="a87cb-1574">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="a87cb-1575">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1575">No</span></span>               |
| <span data-ttu-id="a87cb-1576">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="a87cb-1576">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="a87cb-1577">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="a87cb-1577">2.5.29.14</span></span> | <span data-ttu-id="a87cb-1578">Används för att identifiera en enskild offentlig nyckel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1578">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="a87cb-1579">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1579">No</span></span>               |
| <span data-ttu-id="a87cb-1580">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="a87cb-1580">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="a87cb-1581">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="a87cb-1581">2.5.29.15</span></span> | <span data-ttu-id="a87cb-1582">Innehåller information om giltiga användnings områden för certifikatets offentliga nyckel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1582">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="a87cb-1583">Ja</span><span class="sxs-lookup"><span data-stu-id="a87cb-1583">Yes</span></span>              |
| <span data-ttu-id="a87cb-1584">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="a87cb-1584">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="a87cb-1585">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="a87cb-1585">2.5.29.17</span></span> | <span data-ttu-id="a87cb-1586">Innehåller alternativa DNS-namn för att identifiera certifikatet</span><span class="sxs-lookup"><span data-stu-id="a87cb-1586">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="a87cb-1587">Ja<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="a87cb-1587">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="a87cb-1588">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="a87cb-1588">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="a87cb-1589">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="a87cb-1589">2.5.29.18</span></span> | <span data-ttu-id="a87cb-1590">Innehåller alternativa DNS-namn för att identifiera certifikat utfärdaren</span><span class="sxs-lookup"><span data-stu-id="a87cb-1590">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="a87cb-1591">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1591">No</span></span>               |
| <span data-ttu-id="a87cb-1592">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="a87cb-1592">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="a87cb-1593">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="a87cb-1593">2.5.29.19</span></span> | <span data-ttu-id="a87cb-1594">Tillhandahåller information om grundläggande användnings villkor för certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-1594">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="a87cb-1595">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1595">No</span></span>               |
| <span data-ttu-id="a87cb-1596">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="a87cb-1596">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="a87cb-1597">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="a87cb-1597">2.5.29.30</span></span> | <span data-ttu-id="a87cb-1598">Används för att begränsa certifikat namn till vissa domäner</span><span class="sxs-lookup"><span data-stu-id="a87cb-1598">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="a87cb-1599">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1599">No</span></span>               |
| <span data-ttu-id="a87cb-1600">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="a87cb-1600">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="a87cb-1601">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="a87cb-1601">2.5.29.31</span></span> | <span data-ttu-id="a87cb-1602">Tillhandahåller URI: er för CRL-distribution</span><span class="sxs-lookup"><span data-stu-id="a87cb-1602">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="a87cb-1603">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1603">No</span></span>               |
| <span data-ttu-id="a87cb-1604">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="a87cb-1604">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="a87cb-1605">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="a87cb-1605">2.5.29.32</span></span> | <span data-ttu-id="a87cb-1606">Lista över certifikat principer för stora PKI-system</span><span class="sxs-lookup"><span data-stu-id="a87cb-1606">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="a87cb-1607">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1607">No</span></span>               |
| <span data-ttu-id="a87cb-1608">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="a87cb-1608">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="a87cb-1609">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="a87cb-1609">2.5.29.33</span></span> | <span data-ttu-id="a87cb-1610">Lista över principer för certifikat utfärdare</span><span class="sxs-lookup"><span data-stu-id="a87cb-1610">List of CA certificate policies</span></span>                                                | <span data-ttu-id="a87cb-1611">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1611">No</span></span>               |
| <span data-ttu-id="a87cb-1612">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="a87cb-1612">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="a87cb-1613">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="a87cb-1613">2.5.29.35</span></span> | <span data-ttu-id="a87cb-1614">Används för att identifiera en enskild offentlig nyckel som är kopplad till en certifikatets signatur</span><span class="sxs-lookup"><span data-stu-id="a87cb-1614">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="a87cb-1615">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1615">No</span></span>               |
| <span data-ttu-id="a87cb-1616">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="a87cb-1616">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="a87cb-1617">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="a87cb-1617">2.5.29.36</span></span> | <span data-ttu-id="a87cb-1618">Begränsningar för CA-principer</span><span class="sxs-lookup"><span data-stu-id="a87cb-1618">CA policy constraints</span></span>                                                          | <span data-ttu-id="a87cb-1619">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1619">No</span></span>               |
| <span data-ttu-id="a87cb-1620">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="a87cb-1620">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="a87cb-1621">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="a87cb-1621">2.5.29.37</span></span> | <span data-ttu-id="a87cb-1622">Ytterligare OID-baserad nyckel användnings information</span><span class="sxs-lookup"><span data-stu-id="a87cb-1622">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="a87cb-1623">Ja</span><span class="sxs-lookup"><span data-stu-id="a87cb-1623">Yes</span></span>              |
| <span data-ttu-id="a87cb-1624">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="a87cb-1624">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="a87cb-1625">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="a87cb-1625">2.5.29.46</span></span> | <span data-ttu-id="a87cb-1626">Innehåller information om hur du hämtar delta-CRL: er</span><span class="sxs-lookup"><span data-stu-id="a87cb-1626">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="a87cb-1627">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1627">No</span></span>               |
| <span data-ttu-id="a87cb-1628">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="a87cb-1628">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="a87cb-1629">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="a87cb-1629">2.5.29.54</span></span> | <span data-ttu-id="a87cb-1630">Fältet CA-certifikat indikerar att AnyPolicy inte kan användas</span><span class="sxs-lookup"><span data-stu-id="a87cb-1630">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="a87cb-1631">Inga</span><span class="sxs-lookup"><span data-stu-id="a87cb-1631">No</span></span>               |

<span data-ttu-id="a87cb-1632">OID och mappningar för X. 509-tillägg</span><span class="sxs-lookup"><span data-stu-id="a87cb-1632">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="a87cb-1633">SubjectAltName-tillägget parsas som en del av DNS-namns kontrollen i tjänst nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1633">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1634">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1634">Parameters</span></span>

- <span data-ttu-id="a87cb-1635">**certifikat** Pekare till certifikat som verifieras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1635">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="a87cb-1636">**tillägg** Retur struktur som innehåller tilläggs data pekare och längd.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1636">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="a87cb-1637">**extension_id** OID-heltals mappning från tabellen ovan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1637">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1638">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1638">Return Values</span></span>

- <span data-ttu-id="a87cb-1639">**NX_SUCCESS** (0X00) angivet tillägg-OID hittades och returnerade data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1639">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="a87cb-1640">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 kod för flera byte påträffades (certifikat som inte stöds).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1640">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="a87cb-1641">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) ett inidentifierat ASN. 1-fält påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1641">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1642">**NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) ogiltig ASN. 1-tagg klass påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1642">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1643">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0X192) ogiltigt tillägg påträffades</span><span class="sxs-lookup"><span data-stu-id="a87cb-1643">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="a87cb-1644">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0X19B) det angivna tilläggets OID hittades inte i det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1644">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="a87cb-1645">**NX_PTR_ERROR** (0X07) ogiltig certifikat-eller tilläggs pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1645">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1646">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1646">Allowed From</span></span>

<span data-ttu-id="a87cb-1647">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1647">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1648">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1648">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1649">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1649">See Also</span></span>

- <span data-ttu-id="a87cb-1650">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1650">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="a87cb-1651">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1651">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="a87cb-1652">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1652">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="a87cb-1653">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1653">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="a87cb-1654">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1654">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="a87cb-1655">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1655">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="a87cb-1656">Hitta och parsa ett tillägg för nyckel användning i X. 509 i ett X. 509-certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-1656">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="a87cb-1657">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a87cb-1657">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="a87cb-1658">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1658">Description</span></span>

<span data-ttu-id="a87cb-1659">Den här tjänsten är avsedd att anropas inifrån ett motanrop för certifikat verifiering (se *nx_secure_tls_session_certificate_callback_set)*.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1659">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="a87cb-1660">Den söker efter tillägget för nyckel användning och returnerar den nyckel användnings bitfield som finns i parametern "bitfield".</span><span class="sxs-lookup"><span data-stu-id="a87cb-1660">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="a87cb-1661">Bitarna, som definieras av specifikationen X. 509 (RFC 5280), anges i tabellen nedan.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1661">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="a87cb-1662">En bitvis och med lämplig bitmask (och genom att kontrol lera om det inte är noll) ger värdet för varje bit.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1662">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="a87cb-1663">Observera att DER-encoding för bitfield eliminerar extra nollor, så den faktiska positionen för bitarna i rå certifikat data kommer sannolikt att skilja sig från deras position i den avkodade bitfield.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1663">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="a87cb-1664">De angivna bitmaskna är endast avsedda att användas på de avkodade bitfield som returneras av *nx_secure_x509_key_usage_extension_parse* och inte med RAW der-kodade certifikat data.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1664">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="a87cb-1665">I återanropet av certifikat verifieringen är felet returkod NX_SECURE_X509_KEY_USAGE_ERROR reserverat för användning av program.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1665">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="a87cb-1666">Om det uppstår ett fel när nyckel användningen kontrol leras kan det här värdet returneras från återanropet för att indikera orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1666">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="a87cb-1667">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="a87cb-1667">NetX Secure Identifier</span></span>                            | <span data-ttu-id="a87cb-1668">Bit position</span><span class="sxs-lookup"><span data-stu-id="a87cb-1668">Bit position</span></span> | <span data-ttu-id="a87cb-1669">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a87cb-1669">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a87cb-1670">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="a87cb-1670">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="a87cb-1671">0</span><span class="sxs-lookup"><span data-stu-id="a87cb-1671">0</span></span>            | <span data-ttu-id="a87cb-1672">Certifikat kan användas för digitala signaturer</span><span class="sxs-lookup"><span data-stu-id="a87cb-1672">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="a87cb-1673">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="a87cb-1673">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="a87cb-1674">1</span><span class="sxs-lookup"><span data-stu-id="a87cb-1674">1</span></span>            | <span data-ttu-id="a87cb-1675">Certifikat kan användas för att verifiera digitala signaturer förutom dem för certifikat och CRL: er</span><span class="sxs-lookup"><span data-stu-id="a87cb-1675">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="a87cb-1676">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="a87cb-1676">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="a87cb-1677">2</span><span class="sxs-lookup"><span data-stu-id="a87cb-1677">2</span></span>            | <span data-ttu-id="a87cb-1678">Certifikat kan användas för att kryptera symmetriska nycklar (nyckel transport)</span><span class="sxs-lookup"><span data-stu-id="a87cb-1678">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="a87cb-1679">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="a87cb-1679">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="a87cb-1680">3</span><span class="sxs-lookup"><span data-stu-id="a87cb-1680">3</span></span>            | <span data-ttu-id="a87cb-1681">Certifikat kan användas för att kryptera rå användar data direkt (ovanligt)</span><span class="sxs-lookup"><span data-stu-id="a87cb-1681">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="a87cb-1682">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="a87cb-1682">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="a87cb-1683">4</span><span class="sxs-lookup"><span data-stu-id="a87cb-1683">4</span></span>            | <span data-ttu-id="a87cb-1684">Certifikat kan användas för nyckel avtal (som med Diffie-Hellman)</span><span class="sxs-lookup"><span data-stu-id="a87cb-1684">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="a87cb-1685">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="a87cb-1685">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="a87cb-1686">5</span><span class="sxs-lookup"><span data-stu-id="a87cb-1686">5</span></span>            | <span data-ttu-id="a87cb-1687">Certifikat kan användas för att signera och verifiera andra certifikat (certifikatet är ett CA-eller ICA-certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1687">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="a87cb-1688">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="a87cb-1688">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="a87cb-1689">6</span><span class="sxs-lookup"><span data-stu-id="a87cb-1689">6</span></span>            | <span data-ttu-id="a87cb-1690">Certifikatets offentliga nyckel används för att verifiera signaturer i listor över återkallade certifikat</span><span class="sxs-lookup"><span data-stu-id="a87cb-1690">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="a87cb-1691">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="a87cb-1691">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="a87cb-1692">7</span><span class="sxs-lookup"><span data-stu-id="a87cb-1692">7</span></span>            | <span data-ttu-id="a87cb-1693">Används med nyckel avtals bit (bit 4) – när den anges kan certifikat nyckeln endast användas för kryptering under nyckel avtal.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1693">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="a87cb-1694">Odefinierad om nyckel avtals bit inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1694">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="a87cb-1695">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="a87cb-1695">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="a87cb-1696">8</span><span class="sxs-lookup"><span data-stu-id="a87cb-1696">8</span></span>            | <span data-ttu-id="a87cb-1697">Används med nyckel avtals bit (bit 4) – när den anges kan certifikat nyckeln endast användas för att dekryptera under nyckel avtal.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1697">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="a87cb-1698">Odefinierad om nyckel avtals bit inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1698">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="a87cb-1699">Bitmask och värden för tillägg för nyckel användning i X. 509</span><span class="sxs-lookup"><span data-stu-id="a87cb-1699">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="a87cb-1700">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a87cb-1700">Parameters</span></span>

- <span data-ttu-id="a87cb-1701">**certifikat** Pekare till certifikat som verifieras.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1701">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="a87cb-1702">**bitfield** Returnera hela bitfield från tillägget.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1702">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="a87cb-1703">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a87cb-1703">Return Values</span></span>

- <span data-ttu-id="a87cb-1704">**NX_SUCCESS** (0X00) nyckel användnings tillägg hittades och bitfield returnerades.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1704">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="a87cb-1705">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 kod för flera byte påträffades (certifikat som inte stöds).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1705">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="a87cb-1706">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) ett inidentifierat ASN. 1-fält påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1706">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1707">**NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) ogiltig ASN. 1-tagg klass påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1707">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1708">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0X192) ogiltigt tillägg påträffades (ogiltigt certifikat).</span><span class="sxs-lookup"><span data-stu-id="a87cb-1708">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="a87cb-1709">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0X19B) Det gick inte att hitta nyckel användnings tillägget i det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1709">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="a87cb-1710">**NX_PTR_ERROR** (0X07) ogiltig certifikat-eller bitfield-pekare.</span><span class="sxs-lookup"><span data-stu-id="a87cb-1710">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a87cb-1711">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a87cb-1711">Allowed From</span></span>

<span data-ttu-id="a87cb-1712">Konversation</span><span class="sxs-lookup"><span data-stu-id="a87cb-1712">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a87cb-1713">Exempel</span><span class="sxs-lookup"><span data-stu-id="a87cb-1713">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="a87cb-1714">Se även</span><span class="sxs-lookup"><span data-stu-id="a87cb-1714">See Also</span></span>

- <span data-ttu-id="a87cb-1715">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="a87cb-1715">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="a87cb-1716">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="a87cb-1716">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="a87cb-1717">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1717">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="a87cb-1718">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="a87cb-1718">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="a87cb-1719">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="a87cb-1719">nx_secure_x509_extension_find</span></span>
