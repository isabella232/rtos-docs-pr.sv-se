---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNMP agent-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SNMP agent-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825767"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="11ccd-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNMP agent-tjänster</span><span class="sxs-lookup"><span data-stu-id="11ccd-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="11ccd-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo SNMP agent-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="11ccd-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="11ccd-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="11ccd-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="11ccd-107">*Ange autentiseringsnyckel (endast SNMP v3) för trap-meddelanden*</span><span class="sxs-lookup"><span data-stu-id="11ccd-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="11ccd-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="11ccd-109">*Ange autentiseringsnyckel (endast SNMP v3) för svarsmeddelanden*</span><span class="sxs-lookup"><span data-stu-id="11ccd-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="11ccd-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="11ccd-111">*Hämta community-namn*</span><span class="sxs-lookup"><span data-stu-id="11ccd-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="11ccd-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="11ccd-113">*Ange kontext motor (endast SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="11ccd-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="11ccd-115">*Ange kontext namn (endast SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="11ccd-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="11ccd-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="11ccd-117">*Skapa SNMP-agent*</span><span class="sxs-lookup"><span data-stu-id="11ccd-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="11ccd-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="11ccd-119">*Hämta SNMP-versionen av det mottagna paketet*</span><span class="sxs-lookup"><span data-stu-id="11ccd-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="11ccd-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="11ccd-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="11ccd-121">*Ange om den senaste SNMP-begäran är GET-eller SET-typ*</span><span class="sxs-lookup"><span data-stu-id="11ccd-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="11ccd-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="11ccd-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="11ccd-123">*Avgöra om strängen matchar agentens privata sträng*</span><span class="sxs-lookup"><span data-stu-id="11ccd-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="11ccd-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="11ccd-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="11ccd-125">*Avgöra om strängen matchar den offentliga agentens sträng*</span><span class="sxs-lookup"><span data-stu-id="11ccd-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="11ccd-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="11ccd-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="11ccd-127">*Ange nätverks gränssnitt för SNMP-meddelanden*</span><span class="sxs-lookup"><span data-stu-id="11ccd-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="11ccd-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="11ccd-129">*Ange SNMP-agentens privata grupp sträng*</span><span class="sxs-lookup"><span data-stu-id="11ccd-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="11ccd-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="11ccd-131">*Ange SNMP-agentens offentliga grupp sträng*</span><span class="sxs-lookup"><span data-stu-id="11ccd-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="11ccd-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="11ccd-133">*Ange SNMP-agentens status för alla SNMP-versioner*</span><span class="sxs-lookup"><span data-stu-id="11ccd-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="11ccd-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="11ccd-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="11ccd-135">*Ta bort SNMP-agent*</span><span class="sxs-lookup"><span data-stu-id="11ccd-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="11ccd-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="11ccd-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="11ccd-137">*Skapa en MD5-nyckel (endast SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="11ccd-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="11ccd-139">*Skapa en MD5-nyckel (endast SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="11ccd-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="11ccd-141">*Ange krypterings nyckel (endast SNMP v3) för trap-meddelanden*</span><span class="sxs-lookup"><span data-stu-id="11ccd-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="11ccd-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="11ccd-143">*Ange krypterings nyckel (endast SNMP v3) för svarsmeddelanden*</span><span class="sxs-lookup"><span data-stu-id="11ccd-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="11ccd-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="11ccd-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="11ccd-145">*Skapa SHA-nyckel (endast SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="11ccd-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="11ccd-147">*Skapa SHA-nyckel (endast SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="11ccd-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="11ccd-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="11ccd-149">*Starta SNMP-agenten*</span><span class="sxs-lookup"><span data-stu-id="11ccd-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="11ccd-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="11ccd-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="11ccd-151">*Stoppa SNMP-agenten*</span><span class="sxs-lookup"><span data-stu-id="11ccd-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="11ccd-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="11ccd-153">*Skicka SNMP v1 Trap (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="11ccd-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="11ccd-155">*Skicka SNMP v2 Trap (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="11ccd-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="11ccd-157">*Skicka SNMP v2 Trap (endast IPv4) ange OID*</span><span class="sxs-lookup"><span data-stu-id="11ccd-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="11ccd-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="11ccd-159">*Skicka SNMP v3 Trap (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="11ccd-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="11ccd-161">*Skicka SNMP v2 Trap (endast IPv4) ange OID*</span><span class="sxs-lookup"><span data-stu-id="11ccd-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="11ccd-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="11ccd-163">*Skicka SNMP v1-Trap (IPv4 och IPv6)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="11ccd-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="11ccd-165">*Skicka SNMP v2-Trap (IPv4 och IPv6)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="11ccd-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="11ccd-167">*Skicka SNMP v2 Trap (IPv4/IPv6) som anger OID*</span><span class="sxs-lookup"><span data-stu-id="11ccd-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="11ccd-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="11ccd-169">*Skicka SNMP v3 Trap (IPv4 och IPv6)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="11ccd-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="11ccd-171">*Skicka SNMP v2 Trap (IPv4/IPv6) som anger OID*</span><span class="sxs-lookup"><span data-stu-id="11ccd-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="11ccd-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="11ccd-173">*Ange antal omstarter*</span><span class="sxs-lookup"><span data-stu-id="11ccd-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="11ccd-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="11ccd-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="11ccd-175">*Jämför två objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-175">*Compare two objects*</span></span>
- [<span data-ttu-id="11ccd-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="11ccd-177">*Jämför två objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-177">*Compare two objects*</span></span>
- [<span data-ttu-id="11ccd-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="11ccd-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="11ccd-179">*Kopiera ett objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-179">*Copy an object*</span></span>
- [<span data-ttu-id="11ccd-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="11ccd-181">*Kopiera ett objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-181">*Copy an object*</span></span>
- [<span data-ttu-id="11ccd-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="11ccd-183">*Hämta räknar objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-183">*Get counter object*</span></span>
- [<span data-ttu-id="11ccd-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="11ccd-185">*Ange Counter-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-185">*Set counter object*</span></span>
- [<span data-ttu-id="11ccd-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="11ccd-187">*Hämta 64-bitars räknar objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="11ccd-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="11ccd-189">*Ange 64-bit Counter-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="11ccd-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="11ccd-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="11ccd-191">*Ange värdet för slut punkt för MIB*</span><span class="sxs-lookup"><span data-stu-id="11ccd-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="11ccd-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="11ccd-193">*Hämta mätar objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-193">*Get gauge object*</span></span>
- [<span data-ttu-id="11ccd-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="11ccd-195">*Ange mätar objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-195">*Set gauge object*</span></span>
- [<span data-ttu-id="11ccd-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="11ccd-197">*Hämta objekt-ID*</span><span class="sxs-lookup"><span data-stu-id="11ccd-197">*Get object id*</span></span>
- [<span data-ttu-id="11ccd-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="11ccd-199">*Ange objekt-ID*</span><span class="sxs-lookup"><span data-stu-id="11ccd-199">*Set object id*</span></span>
- [<span data-ttu-id="11ccd-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="11ccd-201">*Hämta heltals objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-201">*Get integer object*</span></span>
- [<span data-ttu-id="11ccd-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="11ccd-203">*Ange heltals objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-203">*Set integer object*</span></span>
- [<span data-ttu-id="11ccd-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="11ccd-205">*Hämta IP-adress-objekt (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="11ccd-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="11ccd-207">*Ange IP-adress-objekt (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="11ccd-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="11ccd-209">*Hämta IP-adress-objekt (endast IPv6)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="11ccd-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="11ccd-211">*Ange IP-adress-objekt (endast IPv6)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="11ccd-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="11ccd-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="11ccd-213">*Ange inget-instans värde*</span><span class="sxs-lookup"><span data-stu-id="11ccd-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="11ccd-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="11ccd-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="11ccd-215">*Värdet hittades inte*</span><span class="sxs-lookup"><span data-stu-id="11ccd-215">*Set not-found value*</span></span>
- [<span data-ttu-id="11ccd-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="11ccd-217">*Hämta oktett-String-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-217">*Get octet string object*</span></span>
- [<span data-ttu-id="11ccd-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="11ccd-219">*Ange oktett-String-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-219">*Set octet string object*</span></span>
- [<span data-ttu-id="11ccd-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="11ccd-221">*Hämta ASCII-String-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="11ccd-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="11ccd-223">*Ange ASCII-String-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="11ccd-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="11ccd-225">*Hämta timetics-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-225">*Get timetics object*</span></span>
- [<span data-ttu-id="11ccd-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="11ccd-227">*Ange timetics-objekt*</span><span class="sxs-lookup"><span data-stu-id="11ccd-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="11ccd-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="11ccd-229">Ange autentiseringsnyckel för trap-meddelanden</span><span class="sxs-lookup"><span data-stu-id="11ccd-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-230">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="11ccd-231">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-231">Description</span></span>

<span data-ttu-id="11ccd-232">Den här tjänsten anger den nyckel som ska användas för att ställa in autentiseringsmetoder i säkerhets huvudet SNMPv3 i trap-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="11ccd-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="11ccd-233">Om du anger ett NX_NULL-värde för nyckeln inaktive ras autentiseringen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="11ccd-234">Nyckeln måste ha skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-234">The key must be previously created.</span></span> <span data-ttu-id="11ccd-235">Se nx_snmp_agent_md5_key_create eller nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="11ccd-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-236">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-236">Input Parameters</span></span>

- <span data-ttu-id="11ccd-237">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-238">**nyckel** Pekare till en tidigare skapad MD5-eller SHA-nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-239">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-239">Return Values</span></span>

- <span data-ttu-id="11ccd-240">Den angivna nyckeln för **NX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="11ccd-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="11ccd-241">**NX_NOT_ENABLED** (0X14) SNMP-säkerhet inaktive rad</span><span class="sxs-lookup"><span data-stu-id="11ccd-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="11ccd-242">**NX_PTR_ERROR** (0X07) ogiltig SNMP-agent pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-243">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-243">Allowed From</span></span>

<span data-ttu-id="11ccd-244">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-245">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="11ccd-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="11ccd-247">Ange autentiseringsnyckel för svarsmeddelanden</span><span class="sxs-lookup"><span data-stu-id="11ccd-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-248">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="11ccd-249">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-249">Description</span></span>

<span data-ttu-id="11ccd-250">Den här tjänsten anger den nyckel som ska användas för autentiseringsmetoder i säkerhets parametern SNMPv3 för alla begär Anden som görs när den har angetts.</span><span class="sxs-lookup"><span data-stu-id="11ccd-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="11ccd-251">Om du anger ett NX_NULL-värde för nyckeln inaktive ras autentiseringen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="11ccd-252">Nyckeln måste ha skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-252">The key must be previously created.</span></span> <span data-ttu-id="11ccd-253">Se nx_snmp_agent_md5_key_create eller nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="11ccd-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-254">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-254">Input Parameters</span></span>

- <span data-ttu-id="11ccd-255">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-256">**nyckel** Pekare till en tidigare skapad MD5-eller SHA-nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-257">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-257">Return Values</span></span>

- <span data-ttu-id="11ccd-258">Den SNMP-nyckel som **NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="11ccd-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="11ccd-259">**NX_NOT_ENABLED** (0X14) SNMP-säkerhet inaktive rad</span><span class="sxs-lookup"><span data-stu-id="11ccd-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="11ccd-260">**NX_PTR_ERROR** (0X07) ogiltig SNMP-agent pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-261">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-261">Allowed From</span></span>

<span data-ttu-id="11ccd-262">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-263">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="11ccd-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="11ccd-265">Hämta community-namn</span><span class="sxs-lookup"><span data-stu-id="11ccd-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-266">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="11ccd-267">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-267">Description</span></span>

<span data-ttu-id="11ccd-268">Den här tjänsten hämtar community-namnet från den senaste SNMP-begäran som tagits emot av SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-269">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-269">Input Parameters</span></span>

- <span data-ttu-id="11ccd-270">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-271">**community_string_ptr** Pekare till en sträng pekare som returnerar SNMP-agentens grupp sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-272">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-272">Return Values</span></span>

- <span data-ttu-id="11ccd-273">**NX_SUCCESS** (0X00) SNMP community get.</span><span class="sxs-lookup"><span data-stu-id="11ccd-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="11ccd-274">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-275">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-275">Allowed From</span></span>

<span data-ttu-id="11ccd-276">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-277">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="11ccd-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="11ccd-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="11ccd-279">Ange om den senaste SNMP-begäran är GET-eller SET-typ</span><span class="sxs-lookup"><span data-stu-id="11ccd-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-280">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="11ccd-281">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-281">Description</span></span>

<span data-ttu-id="11ccd-282">Den här tjänsten anger om den senaste begäran från SNMP-hanteraren är en GET-, GETNEXT-eller GETBULK-eller SET-typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="11ccd-283">Den är avsedd att användas med det användar namn för användar namn som används för att jämföra den mottagna grupp strängen med den offentliga SNMP-agenten om begäran är en GET-typ eller till en privat SNMP-agent om begäran är en UPPSÄTTNINGs typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-284">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-284">Input Parameters</span></span>

- <span data-ttu-id="11ccd-285">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-286">**is_get_type** Pekare för att begära typ status:</span><span class="sxs-lookup"><span data-stu-id="11ccd-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="11ccd-287">NX_TRUE om Hämta typ</span><span class="sxs-lookup"><span data-stu-id="11ccd-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="11ccd-288">NX_FALSE om typ av uppsättning</span><span class="sxs-lookup"><span data-stu-id="11ccd-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-289">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-289">Return Values</span></span>

- <span data-ttu-id="11ccd-290">**NX_SUCCESS** (0x00) returnerade typen</span><span class="sxs-lookup"><span data-stu-id="11ccd-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="11ccd-291">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-292">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-292">Allowed From</span></span>

<span data-ttu-id="11ccd-293">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-294">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="11ccd-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="11ccd-296">Ange kontext motor (endast SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-297">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="11ccd-298">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-298">Description</span></span>

<span data-ttu-id="11ccd-299">Den här tjänsten anger kontext motorn för SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="11ccd-300">Den kan bara användas för SNMPv3-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="11ccd-301">Detta ska anropas innan du skapar säkerhets nycklar om programmet använder autentisering och kryptering, eftersom kontext motorns ID används i processen för att skapa nyckeln.</span><span class="sxs-lookup"><span data-stu-id="11ccd-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="11ccd-302">Annars tillhandahåller NetX Duo SNMP ett standard Sammanhangs motor-ID överst i *nxd_snmp. c:*</span><span class="sxs-lookup"><span data-stu-id="11ccd-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="11ccd-303">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-303">Input Parameters</span></span>

- <span data-ttu-id="11ccd-304">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-305">**context_engine** Pekare till kontextens motor sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="11ccd-306">**context_engine_size** Storlek på kontext motor sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="11ccd-307">Observera att det maximala antalet byte i en kontext motor definieras av NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="11ccd-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-308">Return Values</span></span>

- <span data-ttu-id="11ccd-309">**NX_SUCCESS** (0x00) konfiguration av SNMP-kontexten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="11ccd-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="11ccd-310">**NX_NOT_ENABLED** (0X14) SNMPv3 är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="11ccd-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="11ccd-311">**NX_SNMP_ERROR** (0X100) kontext motor storleks fel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="11ccd-312">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-313">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-313">Allowed From</span></span>

<span data-ttu-id="11ccd-314">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-315">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="11ccd-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="11ccd-317">Ange kontext namn (endast SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-318">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="11ccd-319">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-319">Description</span></span>

<span data-ttu-id="11ccd-320">Den här tjänsten anger kontext namnet för SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="11ccd-321">Den kan bara användas för SNMPv3-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="11ccd-322">Om den inte anropas, kommer NetX Duo SNMP-agenten att lämna kontext namnet tomt.</span><span class="sxs-lookup"><span data-stu-id="11ccd-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-323">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-323">Input Parameters</span></span>

- <span data-ttu-id="11ccd-324">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-325">**context_name** Pekare till kontextens namn sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="11ccd-326">**context_name_size** Storlek på kontext namn sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="11ccd-327">Observera att det maximala antalet byte i ett kontext namn definieras av NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="11ccd-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-328">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-328">Return Values</span></span>

- <span data-ttu-id="11ccd-329">**NX_SUCCESS** (0X00) SNMP-kontexten har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="11ccd-330">**NX_SNMP_ERROR** (0x100) fel i kontext namns storlek.</span><span class="sxs-lookup"><span data-stu-id="11ccd-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="11ccd-331">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-332">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-332">Allowed From</span></span>

<span data-ttu-id="11ccd-333">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-334">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="11ccd-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="11ccd-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="11ccd-336">Skapa SNMP-agent</span><span class="sxs-lookup"><span data-stu-id="11ccd-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-337">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="11ccd-338">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-338">Description</span></span>

<span data-ttu-id="11ccd-339">Den här tjänsten skapar en SNMP-agent på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-340">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-340">Input Parameters</span></span>

- <span data-ttu-id="11ccd-341">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-342">**snmp_agent_name** Pekare till namn strängen för SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="11ccd-343">**ip_ptr** Pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="11ccd-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="11ccd-344">**stack_ptr** Pekare till tråd pekare för tråd till SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="11ccd-345">**stack_size** Stack storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="11ccd-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="11ccd-346">**pool_ptr** Visar standard paketets pool för den här SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="11ccd-347">**snmp_agent_username_process** Funktions pekare till programmets hanterings rutin för användar namn.</span><span class="sxs-lookup"><span data-stu-id="11ccd-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="11ccd-348">**snmp_agent_get_process** Funktions pekare till programmets GET reservering-rutin för hantering av förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="11ccd-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="11ccd-349">**snmp_agent_getnext_process** Funktions pekare till programmets hanterings rutin för GETNEXT-begäran.</span><span class="sxs-lookup"><span data-stu-id="11ccd-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="11ccd-350">**snmp_agent_set_process** Funktions pekare till program hanterings rutinen ange begäran.</span><span class="sxs-lookup"><span data-stu-id="11ccd-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-351">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-351">Return Values</span></span>

- <span data-ttu-id="11ccd-352">**NX_SUCCESS** (0X00) SNMP-agenten har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="11ccd-353">**NX_SNMP_ERROR** (0X100) SNMP-agenten skapa fel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="11ccd-354">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-355">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-355">Allowed From</span></span>

<span data-ttu-id="11ccd-356">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-357">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="11ccd-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="11ccd-359">Hämta SNMP-paketets version</span><span class="sxs-lookup"><span data-stu-id="11ccd-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-360">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="11ccd-361">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-361">Description</span></span>

<span data-ttu-id="11ccd-362">Den här tjänsten hämtar den SNMP-version som parsas från det senaste SNMP-paketet som togs emot.</span><span class="sxs-lookup"><span data-stu-id="11ccd-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-363">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-363">Input Parameters</span></span>

- <span data-ttu-id="11ccd-364">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-365">**version** Pekare till den SNMP-version som har parsats från mottaget SNMP-paket</span><span class="sxs-lookup"><span data-stu-id="11ccd-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-366">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-366">Return Values</span></span>

- <span data-ttu-id="11ccd-367">**NX_SUCCESS** (0X00) lyckad SNMP-version Hämta</span><span class="sxs-lookup"><span data-stu-id="11ccd-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="11ccd-368">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="11ccd-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-369">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-369">Allowed From</span></span>

<span data-ttu-id="11ccd-370">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-371">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="11ccd-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="11ccd-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="11ccd-373">Verifiera att den privata strängen matchar agentens privata sträng</span><span class="sxs-lookup"><span data-stu-id="11ccd-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-374">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="11ccd-375">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-375">Description</span></span>

<span data-ttu-id="11ccd-376">Den här tjänsten jämför den null-avslutade inaktuella grupp strängen med den privata strängen för SNMP-agenten och anger om de matchar.</span><span class="sxs-lookup"><span data-stu-id="11ccd-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-377">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-377">Input Parameters</span></span>

- <span data-ttu-id="11ccd-378">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-379">**community_string** Pekare till sträng som ska jämföras</span><span class="sxs-lookup"><span data-stu-id="11ccd-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="11ccd-380">**is_private** Pekare till resultatet av jämförelsen</span><span class="sxs-lookup"><span data-stu-id="11ccd-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="11ccd-381">NX_TRUE-sträng matchningar</span><span class="sxs-lookup"><span data-stu-id="11ccd-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="11ccd-382">NX_FALSE strängen matchar inte</span><span class="sxs-lookup"><span data-stu-id="11ccd-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-383">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-383">Return Values</span></span>

- <span data-ttu-id="11ccd-384">Jämförelse av **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="11ccd-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="11ccd-385">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="11ccd-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-386">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-386">Allowed From</span></span>

<span data-ttu-id="11ccd-387">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-388">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="11ccd-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="11ccd-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="11ccd-390">Verifiera att den mottagna offentliga strängen matchar agentens offentliga sträng</span><span class="sxs-lookup"><span data-stu-id="11ccd-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-391">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="11ccd-392">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-392">Description</span></span>

<span data-ttu-id="11ccd-393">Den här tjänsten jämför en null-avslutad inmatad grupp sträng med den offentliga SNMP-agentens offentliga sträng och anger om de matchar.</span><span class="sxs-lookup"><span data-stu-id="11ccd-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-394">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-394">Input Parameters</span></span>

- <span data-ttu-id="11ccd-395">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-396">**community_string** Pekare till sträng som ska jämföras</span><span class="sxs-lookup"><span data-stu-id="11ccd-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="11ccd-397">**is_public** Pekare till resultatet av jämförelsen</span><span class="sxs-lookup"><span data-stu-id="11ccd-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="11ccd-398">NX_TRUE-sträng matchningar</span><span class="sxs-lookup"><span data-stu-id="11ccd-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="11ccd-399">NX_FALSE strängen matchar inte</span><span class="sxs-lookup"><span data-stu-id="11ccd-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-400">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-400">Return Values</span></span>

- <span data-ttu-id="11ccd-401">Jämförelse av **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="11ccd-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="11ccd-402">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="11ccd-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-403">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-403">Allowed From</span></span>

<span data-ttu-id="11ccd-404">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-405">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="11ccd-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="11ccd-407">Ange SNMP-agentens status för varje SNMP-version</span><span class="sxs-lookup"><span data-stu-id="11ccd-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-408">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="11ccd-409">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-409">Description</span></span>

<span data-ttu-id="11ccd-410">Den här tjänsten anger status (aktive rad/inaktive rad) för var och en av SNMP-versionerna, v1, v2 och v3 på SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="11ccd-411">Observera att de användar konfigurerbara alternativen, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 och NX_SNMP_DISABLE_V3 åsidosätter dessa körnings tids inställningar.</span><span class="sxs-lookup"><span data-stu-id="11ccd-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="11ccd-412">Som standard är SNMP-agenten aktive rad för alla tre versionerna.</span><span class="sxs-lookup"><span data-stu-id="11ccd-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-413">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-413">Input Parameters</span></span>

- <span data-ttu-id="11ccd-414">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-415">**enabled_v1** Anger aktive rad status för SNMP v1 till på/av.</span><span class="sxs-lookup"><span data-stu-id="11ccd-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="11ccd-416">**enabled_v2** Aktiverar/inaktiverar aktiverade status för SNMP v2.</span><span class="sxs-lookup"><span data-stu-id="11ccd-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="11ccd-417">**enabled_v3** Aktiverar/inaktiverar aktiverade status för SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="11ccd-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-418">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-418">Return Values</span></span>

- <span data-ttu-id="11ccd-419">En lyckad SNMP-version har angetts för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="11ccd-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="11ccd-420">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="11ccd-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-421">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-421">Allowed From</span></span>

<span data-ttu-id="11ccd-422">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-423">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="11ccd-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="11ccd-425">Ange privat sträng för SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="11ccd-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-426">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="11ccd-427">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-427">Description</span></span>

<span data-ttu-id="11ccd-428">Den här tjänsten anger SNMP-agentens privata grupp sträng med den angivna null-indatamängden.</span><span class="sxs-lookup"><span data-stu-id="11ccd-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="11ccd-429">Standardvärdet är NULL (ingen privat sträng uppsättning), så att alla SNMP-paket som tas emot med en "privat" grupp sträng inte godkänns av SNMP-agenten för Läs-/skriv åtkomst.</span><span class="sxs-lookup"><span data-stu-id="11ccd-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="11ccd-430">Indatasträngen måste vara mindre än eller lika med användaren som kan konfigureras NX_SNMP_MAX_USER_NAME-1 (för att tillåta utrymme för null-avslutning).</span><span class="sxs-lookup"><span data-stu-id="11ccd-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-431">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-431">Input Parameters</span></span>

- <span data-ttu-id="11ccd-432">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-433">**community_string** Pekare till den privata strängen som ska tilldelas</span><span class="sxs-lookup"><span data-stu-id="11ccd-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-434">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-434">Return Values</span></span>

- <span data-ttu-id="11ccd-435">**NX_SUCCESS** (0X00) har angett en privat sträng</span><span class="sxs-lookup"><span data-stu-id="11ccd-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="11ccd-436">**NX_SNMP_ERROR_TOOBIG** (0X01) sträng storleken är för stor</span><span class="sxs-lookup"><span data-stu-id="11ccd-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="11ccd-437">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="11ccd-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-438">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-438">Allowed From</span></span>

<span data-ttu-id="11ccd-439">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-440">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="11ccd-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="11ccd-442">Ange offentlig sträng för SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="11ccd-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-443">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="11ccd-444">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-444">Description</span></span>

<span data-ttu-id="11ccd-445">Den här tjänsten anger SNMP-agentens offentliga community-sträng med null-inmatad sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="11ccd-446">Grupp strängen måste vara mindre än eller lika med användaren som kan konfigureras NX_SNMP_MAX_USER_NAME-1 (för att tillåta utrymme för null-avslutning).</span><span class="sxs-lookup"><span data-stu-id="11ccd-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-447">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-447">Input Parameters</span></span>

- <span data-ttu-id="11ccd-448">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-449">**community_string** Pekare till den offentliga strängen som ska tilldelas</span><span class="sxs-lookup"><span data-stu-id="11ccd-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-450">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-450">Return Values</span></span>

- <span data-ttu-id="11ccd-451">**NX_SUCCESS** (0X00) har angett en offentlig sträng</span><span class="sxs-lookup"><span data-stu-id="11ccd-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="11ccd-452">**NX_SNMP_ERROR_TOOBIG** (0X01) sträng storleken är för stor</span><span class="sxs-lookup"><span data-stu-id="11ccd-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="11ccd-453">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="11ccd-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-454">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-454">Allowed From</span></span>

<span data-ttu-id="11ccd-455">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-456">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="11ccd-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="11ccd-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="11ccd-458">Ta bort SNMP-agent</span><span class="sxs-lookup"><span data-stu-id="11ccd-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-459">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-460">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-460">Description</span></span>

<span data-ttu-id="11ccd-461">Den här tjänsten tar bort en tidigare skapad SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-462">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-462">Input Parameters</span></span>

- <span data-ttu-id="11ccd-463">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-464">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-464">Return Values</span></span>

- <span data-ttu-id="11ccd-465">**NX_SUCCESS** (0X00) SNMP-agenten har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="11ccd-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="11ccd-466">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-467">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-467">Allowed From</span></span>

<span data-ttu-id="11ccd-468">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-469">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="11ccd-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="11ccd-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="11ccd-471">Ange Nätverks gränssnittet för SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="11ccd-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-472">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="11ccd-473">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-473">Description</span></span>

<span data-ttu-id="11ccd-474">Den här tjänsten anger SNMP-nätverks gränssnittet för SNMP-agenten som anges av indexet för gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="11ccd-475">Detta är endast användbart för SNMP-värdprogram med NetX Duo 5,6 eller högre som stöder flera nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="11ccd-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="11ccd-476">Standardvärdet om inget värde anges av värden är noll för det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-477">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-477">Input Parameters</span></span>

- <span data-ttu-id="11ccd-478">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-479">**If_index** Index som anger SNMP-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-480">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-480">Return Values</span></span>

- <span data-ttu-id="11ccd-481">**NX_SUCCESS** (0X00) SNMP-gränssnittet har angetts.</span><span class="sxs-lookup"><span data-stu-id="11ccd-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="11ccd-482">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-483">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-483">Allowed From</span></span>

<span data-ttu-id="11ccd-484">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-485">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="11ccd-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="11ccd-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="11ccd-487">Skapa en MD5-nyckel (endast SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-488">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="11ccd-489">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-489">Description</span></span>

<span data-ttu-id="11ccd-490">Den här tjänsten skapar en MD5-nyckel som kan användas för autentisering och kryptering.</span><span class="sxs-lookup"><span data-stu-id="11ccd-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="11ccd-491">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="11ccd-491">This service is deprecated.</span></span> <span data-ttu-id="11ccd-492">Utvecklare uppmanas att migrera till *nx_snmp_agent_md5_key_create_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="11ccd-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-493">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-493">Input Parameters</span></span>

- <span data-ttu-id="11ccd-494">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-495">**lösen ord** Pekare till lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="11ccd-496">**destination_key** Pekare till data struktur för SNMP-nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-497">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-497">Return Values</span></span>

- <span data-ttu-id="11ccd-498">**NX_SUCCESS** (0x00) nyckeln har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="11ccd-499">Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="11ccd-500">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-501">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-501">Allowed From</span></span>

<span data-ttu-id="11ccd-502">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-503">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="11ccd-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="11ccd-505">Skapa en MD5-nyckel (endast SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-506">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="11ccd-507">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-507">Description</span></span>

<span data-ttu-id="11ccd-508">Den här tjänsten skapar en MD5-nyckel som kan användas för autentisering och kryptering.</span><span class="sxs-lookup"><span data-stu-id="11ccd-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="11ccd-509">Den här tjänsten ersätter *nx_snmp_agent_md5_key_create ().*</span><span class="sxs-lookup"><span data-stu-id="11ccd-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="11ccd-510">Den här versionen kräver att anroparen anger lösen ords längd.</span><span class="sxs-lookup"><span data-stu-id="11ccd-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-511">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-511">Input Parameters</span></span>

- <span data-ttu-id="11ccd-512">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-513">**lösen ord** Pekare till lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="11ccd-514">**password_length** Längd på lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="11ccd-515">**destination_key** Pekare till data struktur för SNMP-nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-516">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-516">Return Values</span></span>

- <span data-ttu-id="11ccd-517">**NX_SUCCESS** (0x00) nyckeln har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="11ccd-518">Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="11ccd-519">**NX_SNMP_FAILED** (0X102) SNMP misslyckades.</span><span class="sxs-lookup"><span data-stu-id="11ccd-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="11ccd-520">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-521">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-521">Allowed From</span></span>

<span data-ttu-id="11ccd-522">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-523">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="11ccd-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="11ccd-525">Ange krypterings nyckel för trap-meddelanden</span><span class="sxs-lookup"><span data-stu-id="11ccd-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-526">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="11ccd-527">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-527">Description</span></span>

<span data-ttu-id="11ccd-528">Den här tjänsten anger att en tidigare skapad sekretess nyckel ska användas för kryptering och dekryptering av SNMPv3-trap-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="11ccd-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="11ccd-529">*En authentictation-nyckel måste skapas tidigare. SNMP v3-sekretess (kryptering) kräver autentisering. Se nx_snmp_agent_auth_trap_key_use för mer information.*</span><span class="sxs-lookup"><span data-stu-id="11ccd-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-530">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-530">Input Parameters</span></span>

- <span data-ttu-id="11ccd-531">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-532">**nyckel** Pekare till tidigare skapa nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-533">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-533">Return Values</span></span>

- <span data-ttu-id="11ccd-534">Sekretess nyckeln för **NX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="11ccd-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="11ccd-535">Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="11ccd-536">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-537">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-537">Allowed From</span></span>

<span data-ttu-id="11ccd-538">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-539">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="11ccd-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="11ccd-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="11ccd-541">Ange krypterings nyckel för svarsmeddelanden</span><span class="sxs-lookup"><span data-stu-id="11ccd-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-542">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="11ccd-543">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-543">Description</span></span>

<span data-ttu-id="11ccd-544">Den här tjänsten anger att den tidigare skapade nyckeln ska användas för kryptering och dekryptering av SNMPv3-svarsmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="11ccd-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="11ccd-545">*En autentiseringsnyckel måste anges tidigare. SNMP v3-kryptering kräver också att en autentiseringsnyckel skapas. Se nx_snmp_agent_authentiation_key_use för mer information.*</span><span class="sxs-lookup"><span data-stu-id="11ccd-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-546">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-546">Input Parameters</span></span>

- <span data-ttu-id="11ccd-547">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-548">**nyckel** Pekare till tidigare skapa nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-549">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-549">Return Values</span></span>

- <span data-ttu-id="11ccd-550">Sekretess nyckeln för **NX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="11ccd-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="11ccd-551">Säkerhet för **NX_NOT_ENABLED** (0x14) har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="11ccd-552">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-553">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-553">Allowed From</span></span>

<span data-ttu-id="11ccd-554">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-555">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="11ccd-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="11ccd-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="11ccd-557">Skapa SHA-nyckel (endast SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-558">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="11ccd-559">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-559">Description</span></span>

<span data-ttu-id="11ccd-560">Den här tjänsten skapar en SHA-nyckel som kan användas för autentisering och kryptering.</span><span class="sxs-lookup"><span data-stu-id="11ccd-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="11ccd-561">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="11ccd-561">This service is deprecated.</span></span> <span data-ttu-id="11ccd-562">Utvecklare uppmanas att migrera till *nx_snmp_agent_sha_key_create_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="11ccd-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-563">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-563">Input Parameters</span></span>

- <span data-ttu-id="11ccd-564">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-565">**lösen ord** Pekare till lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="11ccd-566">**destination_key** Pekare till data struktur för SNMP-nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-567">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-567">Return Values</span></span>

- <span data-ttu-id="11ccd-568">**NX_SUCCESS** (0x00) nyckeln har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="11ccd-569">Fel vid skapande av **NX_SNMP_ERROR** (0X100) nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="11ccd-570">**NX_PTR_ERROR** (0X07) ogiltig SNMP-agent eller nyckel pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-571">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-571">Allowed From</span></span>

<span data-ttu-id="11ccd-572">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-573">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="11ccd-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="11ccd-575">Skapa SHA-nyckel (endast SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-576">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="11ccd-577">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-577">Description</span></span>

<span data-ttu-id="11ccd-578">Den här tjänsten skapar en SHA-nyckel som kan användas för autentisering och kryptering.</span><span class="sxs-lookup"><span data-stu-id="11ccd-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="11ccd-579">Den här tjänsten ersätter *nx_snmp_agent_sha_key_create ().*</span><span class="sxs-lookup"><span data-stu-id="11ccd-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="11ccd-580">Den här versionen kräver att anroparen anger lösen ords längd.</span><span class="sxs-lookup"><span data-stu-id="11ccd-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-581">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-581">Input Parameters</span></span>

- <span data-ttu-id="11ccd-582">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-583">**lösen ord** Pekare till lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="11ccd-584">**password_length** Längd på lösen ords sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="11ccd-585">**destination_key** Pekare till data struktur för SNMP-nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-586">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-586">Return Values</span></span>

- <span data-ttu-id="11ccd-587">**NX_SUCCESS** (0x00) nyckeln har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="11ccd-588">Fel vid skapande av **NX_SNMP_ERROR** (0X100) nyckel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="11ccd-589">Det gick inte att skapa nyckeln **NX_SNMP_FAILED** (0x102).</span><span class="sxs-lookup"><span data-stu-id="11ccd-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="11ccd-590">**NX_PTR_ERROR** (0X07) ogiltig SNMP-agent eller nyckel pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-591">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-591">Allowed From</span></span>

<span data-ttu-id="11ccd-592">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-593">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="11ccd-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="11ccd-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="11ccd-595">Starta SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="11ccd-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-596">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-597">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-597">Description</span></span>

<span data-ttu-id="11ccd-598">Den här tjänsten binder UDP-socketen till SNMP-porten 161 och startar uppgiften SNMP agent Thread.</span><span class="sxs-lookup"><span data-stu-id="11ccd-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-599">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-599">Input Parameters</span></span>

- <span data-ttu-id="11ccd-600">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-601">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-601">Return Values</span></span>

- <span data-ttu-id="11ccd-602">**NX_SUCCESS** (0X00) lyckad start av SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="11ccd-603">**NX_SNMP_ERROR** (0X100) SNMP agent start fel.</span><span class="sxs-lookup"><span data-stu-id="11ccd-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="11ccd-604">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-605">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-605">Allowed From</span></span>

<span data-ttu-id="11ccd-606">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-607">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="11ccd-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="11ccd-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="11ccd-609">Stoppa SNMP-agenten</span><span class="sxs-lookup"><span data-stu-id="11ccd-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-610">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-611">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-611">Description</span></span>

<span data-ttu-id="11ccd-612">Den här tjänsten stoppar SNMP-agentens tråd uppgift och avbinder UDP-socketen till SNMP-porten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-613">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-613">Input Parameters</span></span>

- <span data-ttu-id="11ccd-614">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-615">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-615">Return Values</span></span>

- <span data-ttu-id="11ccd-616">**NX_SUCCESS** (0x00) stoppade SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="11ccd-617">**NX_PTR_ERROR** (0X07) ogiltig SNMP-agent pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-618">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-618">Allowed From</span></span>

<span data-ttu-id="11ccd-619">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-620">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="11ccd-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="11ccd-622">Skicka SNMPv1 *-trap (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-623">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="11ccd-624">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-624">Description</span></span>

<span data-ttu-id="11ccd-625">Den här tjänsten skickar en SNMP-trap till SNMP-hanteraren på den angivna IPv4-adressen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="11ccd-626">Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att använda tjänsten *nxd_snmp_agent_trap_send* .</span><span class="sxs-lookup"><span data-stu-id="11ccd-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="11ccd-627">*nx_snmp_agent_trap_send* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-628">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-628">Input Parameters</span></span>

- <span data-ttu-id="11ccd-629">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-630">**ip_address** IPv4-adress för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-631">**Enterprise** ID-sträng för företags objekt (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="11ccd-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="11ccd-632">**trap_type** Typ av trap som begärs, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="11ccd-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="11ccd-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="11ccd-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="11ccd-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="11ccd-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="11ccd-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="11ccd-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="11ccd-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="11ccd-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="11ccd-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="11ccd-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="11ccd-639">**trap_code** Angiven trap-kod.</span><span class="sxs-lookup"><span data-stu-id="11ccd-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="11ccd-640">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-641">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-642">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-643">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-643">Return Values</span></span>

- <span data-ttu-id="11ccd-644">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-645">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-646">**NX_NOT_ENABLED** (0X14) SNMPv1 är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="11ccd-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="11ccd-647">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-648">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-648">Allowed From</span></span>

<span data-ttu-id="11ccd-649">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-650">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="11ccd-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="11ccd-652">Skicka SNMPv1 *-trap (IPv4 och IPv6)*</span><span class="sxs-lookup"><span data-stu-id="11ccd-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-654">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-654">Description</span></span>

<span data-ttu-id="11ccd-655">Den här tjänsten skickar en SNMP-trap till SNMP-hanteraren på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="11ccd-656">Den likvärdiga metoden för att skicka en SNMP-trap i NetX är *nxd_snmp_agent_trap_send* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-657">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-657">Input Parameters</span></span>

- <span data-ttu-id="11ccd-658">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-659">**ip_address** SNMP-hanterarens IPv4-eller IPv6-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-660">**Enterprise** ID-sträng för företags objekt (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="11ccd-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="11ccd-661">**trap_type** Typ av trap som begärs, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="11ccd-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="11ccd-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="11ccd-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="11ccd-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="11ccd-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="11ccd-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="11ccd-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="11ccd-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="11ccd-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="11ccd-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="11ccd-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="11ccd-668">**trap_code** Angiven trap-kod.</span><span class="sxs-lookup"><span data-stu-id="11ccd-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="11ccd-669">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-670">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-671">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-672">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-672">Return Values</span></span>

- <span data-ttu-id="11ccd-673">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-674">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-675">**NX_NOT_ENABLED** (0X14) SNMPv1 är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="11ccd-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="11ccd-676">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-677">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-677">Allowed From</span></span>

<span data-ttu-id="11ccd-678">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-679">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="11ccd-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="11ccd-681">Skicka SNMPv2-Trap (endast IPv4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-682">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-683">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-683">Description</span></span>

<span data-ttu-id="11ccd-684">Den här tjänsten skickar en SNMPv2-trap till SNMP-hanteraren på den angivna IPv4-adressen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="11ccd-685">Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv2_send* .</span><span class="sxs-lookup"><span data-stu-id="11ccd-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="11ccd-686">*nx_snmp_agent_trapv2_send* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-687">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-687">Input Parameters</span></span>

- <span data-ttu-id="11ccd-688">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-689">**ip_address** IPv4-adress för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-690">**Community** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-690">**community** Community name (username).</span></span>
- <span data-ttu-id="11ccd-691">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="11ccd-691">**trap_type**</span></span>  
   <span data-ttu-id="11ccd-692">Typ av trap som begärdes.</span><span class="sxs-lookup"><span data-stu-id="11ccd-692">Type of trap requested.</span></span> <span data-ttu-id="11ccd-693">Standard händelserna är:</span><span class="sxs-lookup"><span data-stu-id="11ccd-693">The standard events are:</span></span>  
   - <span data-ttu-id="11ccd-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="11ccd-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="11ccd-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="11ccd-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="11ccd-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="11ccd-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="11ccd-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="11ccd-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="11ccd-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="11ccd-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="11ccd-700">För patentskyddade data:</span><span class="sxs-lookup"><span data-stu-id="11ccd-700">For proprietary data:</span></span>  
   - <span data-ttu-id="11ccd-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="11ccd-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="11ccd-702">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-703">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-704">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-705">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-705">Return Values</span></span>

- <span data-ttu-id="11ccd-706">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-707">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-708">**NX_NOT_ENABLED** (0X14) SNMPv2 är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="11ccd-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="11ccd-709">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-710">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-710">Allowed From</span></span>

<span data-ttu-id="11ccd-711">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-712">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="11ccd-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="11ccd-714">Skicka SNMPv2-trap genom att ange OID direkt</span><span class="sxs-lookup"><span data-stu-id="11ccd-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-715">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-716">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-716">Description</span></span>

<span data-ttu-id="11ccd-717">Den här tjänsten skickar en SNMPv2-trap till SNMP-hanteraren på den angivna IP-adressen (endast IPv4) och tillåter att anroparen anger OID direkt.</span><span class="sxs-lookup"><span data-stu-id="11ccd-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="11ccd-718">Den bästa metoden för att skicka en SNMP-trap med angivet OID i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv2_oid_send* .</span><span class="sxs-lookup"><span data-stu-id="11ccd-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="11ccd-719">*nx_snmp_agent_trapv2_oid_ skicka* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-720">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-720">Input Parameters</span></span>

- <span data-ttu-id="11ccd-721">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-722">**ip_address** IP-adress för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-723">**Community** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-723">**community** Community name (username).</span></span>
- <span data-ttu-id="11ccd-724">**OID** Pekare till buffert som innehåller OID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="11ccd-725">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-726">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-727">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-728">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-728">Return Values</span></span>

- <span data-ttu-id="11ccd-729">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-730">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-731">**NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="11ccd-732">**NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="11ccd-733">**NX_OPTION_ERROR** (0X0a) ogiltig parameter.</span><span class="sxs-lookup"><span data-stu-id="11ccd-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-734">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-734">Allowed From</span></span>

<span data-ttu-id="11ccd-735">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-736">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="11ccd-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="11ccd-738">Skicka SNMPv2-Trap (IPv4 och IPv6)</span><span class="sxs-lookup"><span data-stu-id="11ccd-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-739">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-740">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-740">Description</span></span>

<span data-ttu-id="11ccd-741">Den här tjänsten skickar en SNMP v2-trap till SNMP-hanteraren på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-742">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-742">Input Parameters</span></span>

- <span data-ttu-id="11ccd-743">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-744">**ip_address** IP-adress (IPv4 eller IPv6) för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-745">**Community** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-745">**community** Community name (username).</span></span>
- <span data-ttu-id="11ccd-746">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="11ccd-746">**trap_type**</span></span>  
   <span data-ttu-id="11ccd-747">Typ av trap som begärdes.</span><span class="sxs-lookup"><span data-stu-id="11ccd-747">Type of trap requested.</span></span> <span data-ttu-id="11ccd-748">Standard händelserna är:</span><span class="sxs-lookup"><span data-stu-id="11ccd-748">The standard events are:</span></span>  
   - <span data-ttu-id="11ccd-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="11ccd-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="11ccd-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="11ccd-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="11ccd-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="11ccd-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="11ccd-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="11ccd-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="11ccd-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="11ccd-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="11ccd-755">För patentskyddade data:</span><span class="sxs-lookup"><span data-stu-id="11ccd-755">For proprietary data:</span></span>

   - <span data-ttu-id="11ccd-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="11ccd-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="11ccd-757">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-758">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-759">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-760">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-760">Return Values</span></span>

- <span data-ttu-id="11ccd-761">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-762">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-763">**NX_NOT_ENABLED** (0X14) SNMPv2 är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="11ccd-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="11ccd-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) en IP-version som inte stöds</span><span class="sxs-lookup"><span data-stu-id="11ccd-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="11ccd-765">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-766">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-766">Allowed From</span></span>

<span data-ttu-id="11ccd-767">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-768">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="11ccd-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="11ccd-770">Skicka SNMPv2-trap genom att ange OID direkt</span><span class="sxs-lookup"><span data-stu-id="11ccd-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-771">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-772">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-772">Description</span></span>

<span data-ttu-id="11ccd-773">Den här tjänsten skickar en SNMP v2-trap till SNMP-hanteraren på den angivna IP-adressen (IPv4/IPv6) och tillåter att anroparen anger OID direkt.</span><span class="sxs-lookup"><span data-stu-id="11ccd-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-774">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-774">Input Parameters</span></span>

- <span data-ttu-id="11ccd-775">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-776">**ip_address** IP-adress för SNMP-hanteraren (IPv4/IPv6).</span><span class="sxs-lookup"><span data-stu-id="11ccd-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="11ccd-777">**Community** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-777">**community** Community name (username).</span></span>
- <span data-ttu-id="11ccd-778">**OID** Pekare till buffert som innehåller OID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="11ccd-779">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-780">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-781">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-782">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-782">Return Values</span></span>

- <span data-ttu-id="11ccd-783">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-784">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-785">**NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="11ccd-786">**NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="11ccd-787">**NX_OPTION_ERROR** (0X0a) ogiltig parameter.</span><span class="sxs-lookup"><span data-stu-id="11ccd-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-788">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-788">Allowed From</span></span>

<span data-ttu-id="11ccd-789">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-790">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="11ccd-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="11ccd-792">Skicka SNMPv3-Trap (endast IPv4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-793">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="11ccd-794">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-794">Description</span></span>

<span data-ttu-id="11ccd-795">Den här tjänsten skickar en SNMPv3-trap till SNMP-hanteraren på den angivna IPv4-adressen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="11ccd-796">Den bästa metoden för att skicka en SNMP-trap i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv3_send* .</span><span class="sxs-lookup"><span data-stu-id="11ccd-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="11ccd-797">*nx_snmp_agent_trapv3_send* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-798">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-798">Input Parameters</span></span>

- <span data-ttu-id="11ccd-799">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-800">**ip_address** IPv4-adress för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-801">**användar namn** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-801">**username** Community name (username).</span></span>
- <span data-ttu-id="11ccd-802">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="11ccd-802">**trap_type**</span></span>  
   <span data-ttu-id="11ccd-803">Typ av trap som begärdes.</span><span class="sxs-lookup"><span data-stu-id="11ccd-803">Type of trap requested.</span></span> <span data-ttu-id="11ccd-804">Standard händelserna är:</span><span class="sxs-lookup"><span data-stu-id="11ccd-804">The standard events are:</span></span>  
   - <span data-ttu-id="11ccd-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="11ccd-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="11ccd-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="11ccd-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="11ccd-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="11ccd-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="11ccd-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="11ccd-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="11ccd-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="11ccd-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="11ccd-811">För patentskyddade data:</span><span class="sxs-lookup"><span data-stu-id="11ccd-811">For proprietary data:</span></span>
   - <span data-ttu-id="11ccd-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="11ccd-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="11ccd-813">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-814">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-815">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-816">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-816">Return Values</span></span>

- <span data-ttu-id="11ccd-817">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-818">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-819">**NX_NOT_ENABLED** (0X14) SNMPv3 är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="11ccd-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="11ccd-820">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-821">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-821">Allowed From</span></span>

<span data-ttu-id="11ccd-822">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-823">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="11ccd-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="11ccd-825">Skicka SNMPv3-trap genom att ange OID direkt</span><span class="sxs-lookup"><span data-stu-id="11ccd-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-826">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-827">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-827">Description</span></span>

<span data-ttu-id="11ccd-828">Den här tjänsten skickar en SNMPv3-trap till SNMP-hanteraren på den angivna IP-adressen (endast IPv4) och tillåter att anroparen anger OID direkt.</span><span class="sxs-lookup"><span data-stu-id="11ccd-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="11ccd-829">Den bästa metoden för att skicka en SNMP-trap med angivet OID i NetX Duo är att använda tjänsten *nxd_snmp_agent_trapv3_oid_send* .</span><span class="sxs-lookup"><span data-stu-id="11ccd-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="11ccd-830">*nx_snmp_agent_trapv3_oid_ skicka* ingår i netx Duo för att stödja befintliga netx SNMP agent-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-831">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-831">Input Parameters</span></span>

- <span data-ttu-id="11ccd-832">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-833">**ip_address** IP-adress för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-834">**användar namn** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-834">**username** Community name (username).</span></span>
- <span data-ttu-id="11ccd-835">**OID** Pekare till buffert som innehåller OID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="11ccd-836">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-837">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-838">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-839">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-839">Return Values</span></span>

- <span data-ttu-id="11ccd-840">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-841">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-842">**NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="11ccd-843">**NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="11ccd-844">**NX_OPTION_ERROR** (0X0a) ogiltig parameter.</span><span class="sxs-lookup"><span data-stu-id="11ccd-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-845">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-845">Allowed From</span></span>

<span data-ttu-id="11ccd-846">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-847">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="11ccd-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="11ccd-849">Skicka SNMPv3-Trap (IPv4 och IPv6)</span><span class="sxs-lookup"><span data-stu-id="11ccd-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-850">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-851">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-851">Description</span></span>

<span data-ttu-id="11ccd-852">Den här tjänsten skickar en SNMP-trap till SNMP-hanteraren på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="11ccd-853">Denna trap är i princip samma som SNMP v2-Trap, förutom att trap-meddelande formatet finns i SNMP v3 PDU.</span><span class="sxs-lookup"><span data-stu-id="11ccd-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-854">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-854">Input Parameters</span></span>

- <span data-ttu-id="11ccd-855">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-856">**ip_address** IP-adress (IPv4 eller IPv6) för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-857">**användar namn** Grupp namn (användar namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-857">**username** Community name (username).</span></span>
- <span data-ttu-id="11ccd-858">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="11ccd-858">**trap_type**</span></span>  
   <span data-ttu-id="11ccd-859">Typ av trap som begärdes.</span><span class="sxs-lookup"><span data-stu-id="11ccd-859">Type of trap requested.</span></span> <span data-ttu-id="11ccd-860">Standard händelserna är:</span><span class="sxs-lookup"><span data-stu-id="11ccd-860">The standard events are:</span></span>
   - <span data-ttu-id="11ccd-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="11ccd-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="11ccd-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="11ccd-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="11ccd-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="11ccd-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="11ccd-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="11ccd-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="11ccd-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="11ccd-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="11ccd-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="11ccd-867">För patentskyddade data:</span><span class="sxs-lookup"><span data-stu-id="11ccd-867">For proprietary data:</span></span>
   - <span data-ttu-id="11ccd-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definieras i *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="11ccd-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="11ccd-869">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-870">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-871">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-872">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-872">Return Values</span></span>

- <span data-ttu-id="11ccd-873">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-874">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-875">**NX_NOT_ENABLED** (0X14) SNMPv3 är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="11ccd-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="11ccd-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) en IP-version som inte stöds</span><span class="sxs-lookup"><span data-stu-id="11ccd-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="11ccd-877">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-878">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-878">Allowed From</span></span>

<span data-ttu-id="11ccd-879">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-880">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="11ccd-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="11ccd-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="11ccd-882">Skicka SNMPv3-trap genom att ange OID direkt</span><span class="sxs-lookup"><span data-stu-id="11ccd-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-883">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="11ccd-884">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-884">Description</span></span>

<span data-ttu-id="11ccd-885">Den här tjänsten skickar en SNMPv3-trap till SNMP-hanteraren på den angivna IP-adressen (IPv4/IPv6) och tillåter att anroparen anger OID direkt.</span><span class="sxs-lookup"><span data-stu-id="11ccd-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-886">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-886">Input Parameters</span></span>

- <span data-ttu-id="11ccd-887">**agent_ptr** Pekare till kontroll block för SNMP-agent.</span><span class="sxs-lookup"><span data-stu-id="11ccd-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="11ccd-888">**ip_address** Pekare till IP-adressen för SNMP-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="11ccd-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="11ccd-889">**användar namn** Användar namn (community-namn).</span><span class="sxs-lookup"><span data-stu-id="11ccd-889">**username** Username (community name).</span></span>
- <span data-ttu-id="11ccd-890">**OID** Pekare till buffert som innehåller OID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="11ccd-891">**elapsed_time** Tids systemet har inträffat (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="11ccd-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="11ccd-892">**object_list_ptr** En matris med objekt och deras associerade värden som ska ingå i SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="11ccd-893">Listan har NX_NULL avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-894">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-894">Return Values</span></span>

- <span data-ttu-id="11ccd-895">**NX_SUCCESS** (0X00) lyckad SNMP-trap-sändning.</span><span class="sxs-lookup"><span data-stu-id="11ccd-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="11ccd-896">**NX_SNMP_ERROR** (0x100) Det gick inte att skicka SNMP-trap.</span><span class="sxs-lookup"><span data-stu-id="11ccd-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="11ccd-897">**NX_PTR_ERROR** (0X16) ogiltig SNMP-agent eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="11ccd-898">**NX_IP_ADDRESS_ERROR** (0X21) ogiltigt mål-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-899">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-899">Allowed From</span></span>

<span data-ttu-id="11ccd-900">Konversation</span><span class="sxs-lookup"><span data-stu-id="11ccd-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-901">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="11ccd-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="11ccd-903">Ange antalet omstarter (om SNMPv3 är aktiverat)</span><span class="sxs-lookup"><span data-stu-id="11ccd-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-904">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="11ccd-905">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-905">Description</span></span>

<span data-ttu-id="11ccd-906">Den här tjänsten anger antalet omstarter som registrerats av SNMP-agenten.</span><span class="sxs-lookup"><span data-stu-id="11ccd-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="11ccd-907">Den här tjänsten är bara tillgänglig om SNMPv3 har Aktiver ATS för SNMP-agenten eftersom start antal endast används i SNMPv3-protokollet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-908">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-908">Input Parameters</span></span>

- <span data-ttu-id="11ccd-909">**agent_ptr** Pekare till kontroll block för SNMP-agent</span><span class="sxs-lookup"><span data-stu-id="11ccd-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="11ccd-910">**startar** Värdet för att ange start antal för SNMP-agenten till</span><span class="sxs-lookup"><span data-stu-id="11ccd-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-911">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-911">Return Values</span></span>

- <span data-ttu-id="11ccd-912">**NX_SUCCESS** (0X00) har angett start antal</span><span class="sxs-lookup"><span data-stu-id="11ccd-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="11ccd-913">**NX_SNMP_ERROR** (0X100) fel vid inställning av start antal</span><span class="sxs-lookup"><span data-stu-id="11ccd-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="11ccd-914">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-915">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-915">Allowed From</span></span>

<span data-ttu-id="11ccd-916">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-917">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="11ccd-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="11ccd-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="11ccd-919">Jämför två objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-920">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="11ccd-921">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-921">Description</span></span>

<span data-ttu-id="11ccd-922">Den här tjänsten jämför det tillhandahållna objekt-ID: t med referens objektets ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="11ccd-923">Båda objekt-ID: n är i ASCII SMI-notation, t. ex. att båda objekten måste börja med ASCII-strängen "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="11ccd-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="11ccd-924">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="11ccd-924">This service is deprecated.</span></span> <span data-ttu-id="11ccd-925">Utvecklare uppmanas att migrera till *nx_snmp_object_compare_extended ().*</span><span class="sxs-lookup"><span data-stu-id="11ccd-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-926">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-926">Input Parameters</span></span>

- <span data-ttu-id="11ccd-927">**objekt** Pekare till objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="11ccd-928">**reference_object** Pekar mot referens objektets ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-929">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-929">Return Values</span></span>

- <span data-ttu-id="11ccd-930">**NX_SUCCESS** (0x00) objektet matchar referens-objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="11ccd-931">**NX_SNMP_NEXT_ENTRY** (0x101) objektet är mindre än referens-objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="11ccd-932">**NX_SNMP_ERROR** (0x100) objektet är större än referens-objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="11ccd-933">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-934">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-934">Allowed From</span></span>

<span data-ttu-id="11ccd-935">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-936">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="11ccd-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="11ccd-938">Jämför två objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-939">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="11ccd-940">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-940">Description</span></span>

<span data-ttu-id="11ccd-941">Den här tjänsten jämför det tillhandahållna objekt-ID: t med referens objektets ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="11ccd-942">Båda objekt-ID: n är i ASCII SMI-notation, t. ex. att båda objekten måste börja med ASCII-strängen "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="11ccd-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="11ccd-943">Den här tjänsten ersätter *nx_snmp_object_compare ().*</span><span class="sxs-lookup"><span data-stu-id="11ccd-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="11ccd-944">Den här versionen kräver att anropare anger längd information.</span><span class="sxs-lookup"><span data-stu-id="11ccd-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-945">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-945">Input Parameters</span></span>

- <span data-ttu-id="11ccd-946">**request_object** Pekare för att begära objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="11ccd-947">**request_object_length** Längd på objekt-ID för begäran.</span><span class="sxs-lookup"><span data-stu-id="11ccd-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="11ccd-948">**reference_object** Pekar mot referens objektets ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="11ccd-949">**reference_object_length** Längden på referens objektets ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-950">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-950">Return Values</span></span>

- <span data-ttu-id="11ccd-951">**NX_SUCCESS** (0x00) objektet matchar referens-objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="11ccd-952">**NX_SNMP_NEXT_ENTRY** (0x101) objektet är mindre än referens-objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="11ccd-953">**NX_SNMP_ERROR** (0x100) objektet är större än referens-objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="11ccd-954">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-955">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-955">Allowed From</span></span>

<span data-ttu-id="11ccd-956">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-957">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="11ccd-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="11ccd-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="11ccd-959">Kopiera ett objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-960">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="11ccd-961">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-961">Description</span></span>

<span data-ttu-id="11ccd-962">Den här tjänsten kopierar källobjektet i ASCII SIM-format till målobjektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="11ccd-963">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="11ccd-963">This service is deprecated.</span></span> <span data-ttu-id="11ccd-964">Utvecklare uppmanas att migrera till *nx_snmp_object_copy_extended ().*</span><span class="sxs-lookup"><span data-stu-id="11ccd-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-965">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-965">Input Parameters</span></span>

- <span data-ttu-id="11ccd-966">**source_object_name** Pekare till käll objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="11ccd-967">**destination_object_name** Pekare till mål objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-968">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-968">Return Values</span></span>

- <span data-ttu-id="11ccd-969">**storlek** Antal byte som kopierats till mål namnet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="11ccd-970">Om ett fel returneras returneras noll.</span><span class="sxs-lookup"><span data-stu-id="11ccd-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-971">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-971">Allowed From</span></span>

<span data-ttu-id="11ccd-972">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-973">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="11ccd-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="11ccd-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="11ccd-975">Kopiera ett objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-976">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="11ccd-977">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-977">Description</span></span>

<span data-ttu-id="11ccd-978">Den här tjänsten kopierar källobjektet i ASCII SIM-format till målobjektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="11ccd-979">Den här tjänsten ersätter *nx_snmp_object_copy ().*</span><span class="sxs-lookup"><span data-stu-id="11ccd-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="11ccd-980">Den här versionen kräver att anropare anger längd information.</span><span class="sxs-lookup"><span data-stu-id="11ccd-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-981">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-981">Input Parameters</span></span>

- <span data-ttu-id="11ccd-982">**source_object_name** Pekare till käll objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="11ccd-983">**source_object_name_length** Längd på käll objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="11ccd-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="11ccd-984">**destination_object_name_buffer** Pekare till mål objektets buffert.</span><span class="sxs-lookup"><span data-stu-id="11ccd-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="11ccd-985">**destination_object_name_buffer_size** Storlek på mål objektets buffert.</span><span class="sxs-lookup"><span data-stu-id="11ccd-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-986">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-986">Return Values</span></span>

- <span data-ttu-id="11ccd-987">**storlek** Antal byte som kopierats till mål namnet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="11ccd-988">Om ett fel returneras returneras noll.</span><span class="sxs-lookup"><span data-stu-id="11ccd-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-989">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-989">Allowed From</span></span>

<span data-ttu-id="11ccd-990">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-991">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="11ccd-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="11ccd-993">Hämta räknar objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-994">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="11ccd-995">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-995">Description</span></span>

<span data-ttu-id="11ccd-996">Den här tjänsten hämtar Counter-objektet på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-997">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-998">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-998">Input Parameters</span></span>

- <span data-ttu-id="11ccd-999">**source_ptr** Pekare till räknar källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="11ccd-1000">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1001">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1001">Return Values</span></span>

- <span data-ttu-id="11ccd-1002">**NX_SUCCESS** (0X00) som Counter-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1003">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1004">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1004">Allowed From</span></span>

<span data-ttu-id="11ccd-1005">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1006">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="11ccd-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="11ccd-1008">Ange Counter-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1009">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1010">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1010">Description</span></span>

<span data-ttu-id="11ccd-1011">Den här tjänsten anger räknaren på den adress som anges av mål pekaren med räknarvärdet i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1012">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1013">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1013">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1014">**destination_ptr** Pekare till Counter-mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="11ccd-1015">**object_data** Pekare till käll objekt struktur för räknare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1016">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1016">Return Values</span></span>

- <span data-ttu-id="11ccd-1017">**NX_SUCCESS** (0x00) Counter-objektet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="11ccd-1018">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1019">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1020">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1020">Allowed From</span></span>

<span data-ttu-id="11ccd-1021">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1022">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="11ccd-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="11ccd-1024">Hämta 64-bitars räknar objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1025">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1026">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1026">Description</span></span>

<span data-ttu-id="11ccd-1027">Den här tjänsten hämtar objektet 64-bit Counter på den adress som anges av käll pekaren och placerar den i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1028">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1029">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1029">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1030">**source_ptr** Pekare till räknar källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="11ccd-1031">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1032">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1032">Return Values</span></span>

- <span data-ttu-id="11ccd-1033">**NX_SUCCESS** (0X00) som Counter-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1034">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1035">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1035">Allowed From</span></span>

<span data-ttu-id="11ccd-1036">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1037">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="11ccd-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="11ccd-1039">Ange 64-bit Counter-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1040">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="11ccd-1041">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1041">Description</span></span>

<span data-ttu-id="11ccd-1042">Den här tjänsten ställer in 64-bitars räknaren på den adress som anges av mål pekaren med räknarvärdet i objekt data strukturen NetX.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1043">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1044">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1044">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1045">**destination_ptr** Pekare till Counter-mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="11ccd-1046">**object_data** Pekare till käll objekt struktur för räknare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1047">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1047">Return Values</span></span>

- <span data-ttu-id="11ccd-1048">**NX_SUCCESS** (0x00) Counter-objektet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="11ccd-1049">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1050">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1051">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1051">Allowed From</span></span>

<span data-ttu-id="11ccd-1052">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1053">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="11ccd-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="11ccd-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="11ccd-1055">Ange värdet för slut punkt för MIB</span><span class="sxs-lookup"><span data-stu-id="11ccd-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1056">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1057">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1057">Description</span></span>

<span data-ttu-id="11ccd-1058">Den här tjänsten skapar ett objekt som signalerar slutet av MIB och som vanligt vis anropas från rutinen hämta eller GETNEXT program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1059">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1059">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1060">**not_used_ptr** Visaren har inte använts – bör vara NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="11ccd-1061">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1062">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1062">Return Values</span></span>

- <span data-ttu-id="11ccd-1063">**NX_SUCCESS** (0x00) objekt End-of-MIB-objektet har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="11ccd-1064">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1065">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1065">Allowed From</span></span>

<span data-ttu-id="11ccd-1066">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1067">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="11ccd-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="11ccd-1069">Hämta mätar objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1070">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1071">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1071">Description</span></span>

<span data-ttu-id="11ccd-1072">Den här tjänsten hämtar mätar objektet på den adress som anges av käll pekaren och placerar den i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1073">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1074">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1074">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1075">**source_ptr** Pekare till mätar källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="11ccd-1076">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1077">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1077">Return Values</span></span>

- <span data-ttu-id="11ccd-1078">**NX_SUCCESS** (0X00) Det gick inte att hämta mätar objektet.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1079">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1080">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1080">Allowed From</span></span>

<span data-ttu-id="11ccd-1081">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1082">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="11ccd-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="11ccd-1084">Ange mätar objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1085">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1086">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1086">Description</span></span>

<span data-ttu-id="11ccd-1087">Den här tjänsten ställer in mätaren på den adress som anges av destinations pekaren med mätar värdet i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1088">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1089">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1089">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1090">**destination_ptr** Pekar mot mätar mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="11ccd-1091">**object_data** Pekare för att mäta käll objekt strukturen.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1092">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1092">Return Values</span></span>

- <span data-ttu-id="11ccd-1093">**NX_SUCCESS** (0X00) som mätar objektet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="11ccd-1094">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1095">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1096">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1096">Allowed From</span></span>

<span data-ttu-id="11ccd-1097">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1098">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="11ccd-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="11ccd-1100">Hämta objekt-ID</span><span class="sxs-lookup"><span data-stu-id="11ccd-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1101">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1102">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1102">Description</span></span>

<span data-ttu-id="11ccd-1103">Den här tjänsten hämtar objekt-ID (i ASCII SIM-format) på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1104">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1105">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1105">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1106">**source_ptr** Pekare till objekt-ID-källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="11ccd-1107">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1108">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1108">Return Values</span></span>

- <span data-ttu-id="11ccd-1109">**NX_SUCCESS** (0x00) objekt-ID: t har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1110">**NX_SNMP_ERROR** (0X100) ogiltig längd på objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="11ccd-1111">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1112">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1112">Allowed From</span></span>

<span data-ttu-id="11ccd-1113">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1114">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="11ccd-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="11ccd-1116">Ange objekt-ID</span><span class="sxs-lookup"><span data-stu-id="11ccd-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1117">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1118">Description</span></span>

<span data-ttu-id="11ccd-1119">Den här tjänsten anger objekt-ID (i ASCII SIM-format) på den adress som anges av mål pekaren med objekt-ID: t i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1120">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1121">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1121">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1122">**destination_ptr** Pekar mot objekt-ID-mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="11ccd-1123">**object_data** Pekare till objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1124">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1124">Return Values</span></span>

- <span data-ttu-id="11ccd-1125">**NX_SUCCESS** (0x00) objekt-ID: t har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1126">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1127">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1128">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1128">Allowed From</span></span>

<span data-ttu-id="11ccd-1129">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1130">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="11ccd-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="11ccd-1132">Hämta heltals objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1133">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1134">Description</span></span>

<span data-ttu-id="11ccd-1135">Den här tjänsten hämtar Integer-objektet på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1136">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1137">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1137">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1138">**source_ptr** Pekare till heltals källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="11ccd-1139">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1140">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1140">Return Values</span></span>

- <span data-ttu-id="11ccd-1141">**NX_SUCCESS** (0X00) som heltals objekt har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1142">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1143">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1143">Allowed From</span></span>

<span data-ttu-id="11ccd-1144">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1145">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="11ccd-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="11ccd-1147">Ange heltals objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1148">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1149">Description</span></span>

<span data-ttu-id="11ccd-1150">Den här tjänsten ställer in heltalet på den adress som anges av mål pekaren med heltal svärdet i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1151">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1152">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1152">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1153">**destination_ptr** Pekar mot heltals mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="11ccd-1154">**object_data** Pekare till objekt strukturen med en heltals källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1155">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1155">Return Values</span></span>

- <span data-ttu-id="11ccd-1156">**NX_SUCCESS** (0x00) heltals objekt har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1157">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1158">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1159">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1159">Allowed From</span></span>

<span data-ttu-id="11ccd-1160">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1161">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="11ccd-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="11ccd-1163">Hämta IP-adress-objekt (endast IPv4)</span><span class="sxs-lookup"><span data-stu-id="11ccd-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-1164">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1165">Description</span></span>

<span data-ttu-id="11ccd-1166">Den här tjänsten hämtar objektet IP-adress på den adress som anges av käll pekaren och placerar det i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1167">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1168">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1168">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1169">**source_ptr** Pekare till IPv4-adress källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="11ccd-1170">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1171">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1171">Return Values</span></span>

- <span data-ttu-id="11ccd-1172">**NX_SUCCESS** (0X00) IP-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1173">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1174">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1174">Allowed From</span></span>

<span data-ttu-id="11ccd-1175">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1176">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="11ccd-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="11ccd-1178">Hämta IP-adress-objekt (endast IPv6)</span><span class="sxs-lookup"><span data-stu-id="11ccd-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="11ccd-1179">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1180">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1180">Description</span></span>

<span data-ttu-id="11ccd-1181">Den här tjänsten hämtar IPv6-adressprefixet på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="11ccd-1182">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1183">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1183">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1184">**source_ptr** Pekare till IPv6-adress källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="11ccd-1185">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1186">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1186">Return Values</span></span>

- <span data-ttu-id="11ccd-1187">**NX_SUCCESS** (0X00) IP-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1188">**NX_SNMP_ERROR_WRONGTYPE** (0X07) felaktig kod för inmatad SNMP-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="11ccd-1189">**NX_NOT_ENABLED** (0X14) IPv6 är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="11ccd-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="11ccd-1190">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1191">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1191">Allowed From</span></span>

<span data-ttu-id="11ccd-1192">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1193">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="11ccd-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="11ccd-1195">Ange IPv4-adress objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1196">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1197">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1197">Description</span></span>

<span data-ttu-id="11ccd-1198">Den här tjänsten anger IPv4-adressen på den adress som anges av mål pekaren med IP-adressen i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1199">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1200">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1200">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1201">**destination_ptr** Pekare till IP-adress att ange.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="11ccd-1202">**object_data** Pekare till objekt strukturen IP-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1203">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1203">Return Values</span></span>

- <span data-ttu-id="11ccd-1204">**NX_SUCCESS** (0X00) IP-adressprefixet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1205">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1206">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1207">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1207">Allowed From</span></span>

<span data-ttu-id="11ccd-1208">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1209">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="11ccd-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="11ccd-1211">Ange IPv6-adress objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1212">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1213">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1213">Description</span></span>

<span data-ttu-id="11ccd-1214">Den här tjänsten anger IPv6-adressen på den adress som anges av mål pekaren med IP-adressen i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1215">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1216">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1216">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1217">**destination_ptr** Pekare till IP-adress att ange.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="11ccd-1218">**object_data** Pekare till objekt strukturen IP-adress.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1219">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1219">Return Values</span></span>

- <span data-ttu-id="11ccd-1220">**NX_SUCCESS** (0X00) IPv6-adressen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1221">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1222">**NX_NOT_ENABLED** (0X14) IPv6 är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="11ccd-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="11ccd-1223">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1224">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1224">Allowed From</span></span>

<span data-ttu-id="11ccd-1225">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1226">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="11ccd-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="11ccd-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="11ccd-1228">Ange inget instans objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1229">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1230">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1230">Description</span></span>

<span data-ttu-id="11ccd-1231">Den här tjänsten skapar ett objekt som signalerar att det inte fanns någon instans av det angivna objektet och som vanligt vis anropas från rutinen hämta eller GETNEXT program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1232">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1232">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1233">**not_used_ptr** Visaren har inte använts – bör vara NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="11ccd-1234">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1235">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1235">Return Values</span></span>

- <span data-ttu-id="11ccd-1236">**NX_SUCCESS** (0x00) objektet nr-instance har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="11ccd-1237">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1238">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1238">Allowed From</span></span>

<span data-ttu-id="11ccd-1239">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1240">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="11ccd-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="11ccd-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="11ccd-1242">Det gick inte att hitta objektet</span><span class="sxs-lookup"><span data-stu-id="11ccd-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1243">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1244">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1244">Description</span></span>

<span data-ttu-id="11ccd-1245">Den här tjänsten skapar ett objekt som signalerar att objektet inte hittades och att det vanligt vis anropas från rutinen hämta eller GETNEXT program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1246">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1246">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1247">**not_used_ptr** Visaren har inte använts – bör vara NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="11ccd-1248">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1249">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1249">Return Values</span></span>

- <span data-ttu-id="11ccd-1250">**NX_SUCCESS** (0x00) objektet som inte hittades har skapats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="11ccd-1251">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1252">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1252">Allowed From</span></span>

<span data-ttu-id="11ccd-1253">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1254">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="11ccd-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="11ccd-1256">Hämta oktett-String-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1257">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="11ccd-1258">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1258">Description</span></span>

<span data-ttu-id="11ccd-1259">Den här tjänsten hämtar oktett-strängen på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1260">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1261">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1261">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1262">**source_ptr** Pekare till oktett-sträng källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="11ccd-1263">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="11ccd-1264">**längd** Antal byte i oktett-sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1265">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1265">Return Values</span></span>

- <span data-ttu-id="11ccd-1266">**NX_SUCCESS** (0x00) strängen för oktett-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1267">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1268">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1268">Allowed From</span></span>

<span data-ttu-id="11ccd-1269">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1270">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="11ccd-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="11ccd-1272">Ange oktett-String-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1273">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1274">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1274">Description</span></span>

<span data-ttu-id="11ccd-1275">Den här tjänsten anger oktett-strängen på den adress som anges av mål pekaren med oktett-strängen i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1276">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1277">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1277">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1278">**destination_ptr** Pekare till oktett-sträng mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="11ccd-1279">**object_data** Pekare till oktettens objekt struktur för sträng källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1280">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1280">Return Values</span></span>

- <span data-ttu-id="11ccd-1281">**NX_SUCCESS** (0x00) strängen för oktett-objektet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1282">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1283">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1284">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1284">Allowed From</span></span>

<span data-ttu-id="11ccd-1285">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1286">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="11ccd-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="11ccd-1288">Hämta ASCII-String-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1289">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1290">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1290">Description</span></span>

<span data-ttu-id="11ccd-1291">Den här tjänsten hämtar ASCII-strängen på den adress som anges av käll pekaren och placerar den i NetX-objektets data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1292">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1293">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1293">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1294">**source_ptr** Pekar till ASCII-sträng källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="11ccd-1295">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1296">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1296">Return Values</span></span>

- <span data-ttu-id="11ccd-1297">**NX_SUCCESS** (0X00) ASCII-String-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1298">**NX_SNMP_ERRORs** strängen (0x100) är för stor</span><span class="sxs-lookup"><span data-stu-id="11ccd-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="11ccd-1299">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1300">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1300">Allowed From</span></span>

<span data-ttu-id="11ccd-1301">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1302">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="11ccd-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="11ccd-1304">Ange ASCII-String-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1305">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1306">Description</span></span>

<span data-ttu-id="11ccd-1307">Den här tjänsten anger ASCII-strängen på den adress som anges av mål pekaren med ASCII-strängen i NetX objekt data struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1308">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1309">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1309">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1310">**destination_ptr** Pekar mot ASCII-sträng mål.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="11ccd-1311">**object_data** Pekar till käll objekts struktur för ASCII-sträng.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1312">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1312">Return Values</span></span>

- <span data-ttu-id="11ccd-1313">**NX_SUCCESS** (0X00) ASCII-String-objektet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1314">**NX_SNMP_ERRORs** strängen (0x100) är för stor.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="11ccd-1315">**NX_SNMP_ERROR_BADVALUE** (0X03) ogiltigt tecken i strängen</span><span class="sxs-lookup"><span data-stu-id="11ccd-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="11ccd-1316">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1317">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1318">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1318">Allowed From</span></span>

<span data-ttu-id="11ccd-1319">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1320">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="11ccd-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="11ccd-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="11ccd-1322">Hämta timetics-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1323">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1324">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1324">Description</span></span>

<span data-ttu-id="11ccd-1325">Den här tjänsten hämtar timetics på den adress som anges av käll pekaren och placerar den i data strukturen NetX Object.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="11ccd-1326">Den här rutinen kallas vanligt vis för återanrop från GET-eller GETNEXT-program.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1327">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1327">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1328">**source_ptr** Pekare till timetics-källa.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="11ccd-1329">**object_data** Pekare till målets objekt struktur.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1330">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1330">Return Values</span></span>

- <span data-ttu-id="11ccd-1331">**NX_SUCCESS** (0x00) timetics-objektet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="11ccd-1332">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1333">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1333">Allowed From</span></span>

<span data-ttu-id="11ccd-1334">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1335">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="11ccd-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="11ccd-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="11ccd-1337">Ange timetics-objekt</span><span class="sxs-lookup"><span data-stu-id="11ccd-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="11ccd-1338">Prototyp</span><span class="sxs-lookup"><span data-stu-id="11ccd-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="11ccd-1339">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11ccd-1339">Description</span></span>

<span data-ttu-id="11ccd-1340">Den här tjänsten anger timetics-variabeln på den adress som anges av mål pekaren med timetics i objekt data strukturen NetX.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="11ccd-1341">Den här rutinen kallas vanligt vis för att ange program återanrop.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="11ccd-1342">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1342">Input Parameters</span></span>

- <span data-ttu-id="11ccd-1343">**destination_ptr** Pekare till timetics-destination.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="11ccd-1344">**object_data** Pekare till käll objekts strukturen timetics.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="11ccd-1345">Retur värden</span><span class="sxs-lookup"><span data-stu-id="11ccd-1345">Return Values</span></span>

- <span data-ttu-id="11ccd-1346">**NX_SUCCESS** (0x00) timetics-objektet har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="11ccd-1347">**NX_SNMP_ERROR_WRONGTYPE** (0X07) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="11ccd-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="11ccd-1348">**NX_PTR_ERROR** (0X07) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="11ccd-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="11ccd-1349">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="11ccd-1349">Allowed From</span></span>

<span data-ttu-id="11ccd-1350">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="11ccd-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="11ccd-1351">Exempel</span><span class="sxs-lookup"><span data-stu-id="11ccd-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```