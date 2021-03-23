---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DHCP Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DHCP Client-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826118"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="d9c5d-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DHCP Client Services</span><span class="sxs-lookup"><span data-stu-id="d9c5d-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="d9c5d-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DHCP Client-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="d9c5d-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="d9c5d-106">**nx_dhcp_create**: *skapa en DHCP-instans*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="d9c5d-107">**nx_dhcp_clear_broadcast_flag**: *Rensa sändnings flagga på klient meddelanden*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="d9c5d-108">**nx_dhcp_delete**: *ta bort en DHCP-instans*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="d9c5d-109">**nx_dhcp_force_renew**: *Skicka ett meddelande om Force-förnyelse*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="d9c5d-110">**nx_dhcp_packet_pool_set**: *ange DHCP-klient paketets adresspool*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="d9c5d-111">**nx_dhcp_decline**: skicka *neka meddelande till Server*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="d9c5d-112">**nx_dhcp_release**: Skicka ett *release-meddelande till servern*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="d9c5d-113">**nx_dhcp_reinitialize**: *ta bort nätverks parametrar för DHCP-klienter*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="d9c5d-114">**nx_dhcp_request_client_ip**: *Ange en speciell IP-adress*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="d9c5d-115">**nx_dhcp_send_request**: *Skicka DHCP-meddelande till Server*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="d9c5d-116">**nx_dhcp_start**: *Starta DHCP-klient bearbetningen*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="d9c5d-117">**nx_dhcp_stop**: *stoppa DHCP-klient bearbetningen*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="d9c5d-118">**nx_dhcp_set_interface_index**: *ange gränssnittet för att köra DHCP-klienten*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="d9c5d-119">**nx_dhcp_server_address_get**: *Hämta IP-adressen för DHCP-servern*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="d9c5d-120">**nx_dhcp_state_change_notify**: *Ange callback-funktionen när DHCP-tillstånd ändras*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="d9c5d-121">**nx_dhcp_user_option_retrieve**: *Hämta det angivna DHCP-alternativet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="d9c5d-122">**nx_dhcp_user_option_convert**: *konvertera fyra byte till ulong*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="d9c5d-123">Gränssnitt för vissa DHCP-klient tjänster:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="d9c5d-124">**nx_dhcp_interface_clear_broadcast_flag**: *Rensa sändnings flagga på klient meddelanden i angivet gränssnitt*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="d9c5d-125">**nx_dhcp_interface_enable**: *Aktivera gränssnitt för att köra DHCP på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-126">**nx_dhcp_interface_disable**: *inaktivera gränssnittet för att köra DHCP på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-127">**nx_dhcp_interface_decline**: *Skicka neka meddelande till server på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-128">**nx_dhcp_interface_force_renew**: *Skicka ett Force renew-meddelande på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-129">**nx_dhcp_interface_reinitialize**: *ta bort nätverks parametrar för DHCP-klienter på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-130">**nx_dhcp_interface_release**: *Skicka ett release-meddelande till servern på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-131">**nx_dhcp_interface_request_client_ip**: *Ange en specifik IP-adress för det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-132">**nx_dhcp_interface_send_request**: *Skicka DHCP-meddelande till servern på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-133">**nx_dhcp_interface_server_address_get**: *Hämta IP-adressen för DHCP-servern på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-134">**nx_dhcp_interface_start**: *Starta DHCP-klient bearbetningen på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-135">**nx_dhcp_interface_stop**: *stoppa DHCP-klientens bearbetning på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-136">**nx_dhcp_interface_state_change_notify**: *Ange callback-funktionen när DHCP-tillstånd ändras på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-137">**nx_dhcp_interface_user_option_retrieve**: *Hämta det angivna DHCP-alternativet på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="d9c5d-138">DHCP-klienttjänster om NX_DHCP_CLIENT_RESORE_STATE definieras:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="d9c5d-139">**nx_dhcp_resume**: *återuppta tidigare upprättat DHCP-klient tillstånd*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="d9c5d-140">**nx_dhcp_suspend**: *pausa bearbetningen av DHCP-klientens tillstånd*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="d9c5d-141">**nx_dhcp_client_get_record**: *skapa en post för DHCP-klientens tillstånd*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="d9c5d-142">**nx_dhcp_client_restore_record**: *återställa en tidigare sparad post till DHCP-klienten*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="d9c5d-143">**nx_dhcp_client_update_time_remaining**: *Uppdatera tiden som återstår i det aktuella DHCP-läget*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="d9c5d-144">Gränssnitt för klient tjänster för DHCP om NX_DHCP_CLIENT_RESORE_STATE definieras:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="d9c5d-145">**nx_dhcp_client_interface_get_record**: *skapa en post av DHCP-klientens tillstånd på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-146">**nx_dhcp_client_interface_restore_record**: *Återställ en tidigare sparad post till DHCP-klienten på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="d9c5d-147">**nx_dhcp_client_interface_update_time_remaining**: *Uppdatera tiden som återstår i det aktuella DHCP-läget på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="d9c5d-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="d9c5d-148">nx_dhcp_create</span></span>

<span data-ttu-id="d9c5d-149">Skapa en DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="d9c5d-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-150">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-151">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-151">Description</span></span>

<span data-ttu-id="d9c5d-152">Den här tjänsten skapar en DHCP-instans för den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="d9c5d-153">Som standard är det primära gränssnittet aktiverat för att köra DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="d9c5d-154">Inmatade namn, men som inte används i NetX Duo-implementeringen av DHCP-klienten, måste följa RFC 1035-kriterier för värdnamn.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="d9c5d-155">Den totala längden får inte överskrida 255 tecken, etiketter åtskilda av punkter måste börja med en bokstav och sluta med en bokstav eller siffra och får innehålla bindestreck, men inte andra icke-alfanumeriska tecken.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="d9c5d-156">Om programmet vill köra ett annat gränssnitt som registrerats med IP-instansen (med *nx_ip_interface_attach*) kan programmet anropa *nx_dhcp_set_interface_index* för att köra DHCP på bara det gränssnittet, eller *nx_dhcp_interface_enable* för att köra DHCP på det gränssnittet också.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="d9c5d-157">Mer information finns i Beskrivning av dessa tjänster.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="d9c5d-158">Programmet måste se till att nytto lasten i DHCP-adresspoolen har stöd för den minsta storleken för DHCP-meddelanden som anges i RFC 2131 avsnitt 2 (548 byte av DHCP-meddelande data samt UDP, IP och fysiska nätverks ram rubriker).</span><span class="sxs-lookup"><span data-stu-id="d9c5d-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-159">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-159">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-160">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="d9c5d-161">**ip_ptr**: pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="d9c5d-162">**name_ptr**: pekare till värd namnet för DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-163">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-163">Return Values</span></span>

- <span data-ttu-id="d9c5d-164">**NX_SUCCESS**: (0X00) lyckad DHCP-skapande</span><span class="sxs-lookup"><span data-stu-id="d9c5d-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="d9c5d-165">**NX_DHCP_INVALID_NAME**: (0XA8) ogiltigt värdnamn</span><span class="sxs-lookup"><span data-stu-id="d9c5d-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="d9c5d-166">**NX_DHCP_INVALID_PAYLOAD**: (0X9C) nytto lasten är för liten för DHCP-meddelande</span><span class="sxs-lookup"><span data-stu-id="d9c5d-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="d9c5d-167">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-168">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-168">Allowed From</span></span>

<span data-ttu-id="d9c5d-169">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="d9c5d-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="d9c5d-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="d9c5d-172">Aktivera det angivna gränssnittet för att köra DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="d9c5d-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-174">Description</span></span>

<span data-ttu-id="d9c5d-175">Den här tjänsten aktiverar det angivna gränssnittet för att köra DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="d9c5d-176">Som standard är det primära gränssnittet aktiverat för DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="d9c5d-177">I det här läget kan du starta DHCP på det här gränssnittet antingen genom att anropa *nx_dhcp_interface_start* eller starta DHCP på alla aktiverade gränssnitt *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="d9c5d-178">Programmet måste först registrera det här gränssnittet med IP-instansen med hjälp av *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="d9c5d-179">Vidare måste det finnas ett tillgängligt DHCP-klient gränssnitt för att lägga till det här gränssnittet i listan över aktiverade gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="d9c5d-180">Som standard har NX_DHCP_CLIENT_MAX_RECORDS definierats till 1.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="d9c5d-181">Ange det här alternativet till det maximala antalet gränssnitt som förväntas köra DHCP-klienten samtidigt.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="d9c5d-182">Vanligt vis är NX_DHCP_CLIENT_MAX_RECORDS samma NX_MAX_PHYSICAL_INTERFACES; men om en enhet har fler fysiska gränssnitt än det förväntar sig att köra DHCP-klienten, kan du spara minne genom att ange NX_DHCP_CLIENT_MAX_RECORDS till mindre än det numret.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="d9c5d-183">Det finns inte någon till en mappning av fysiska gränssnitt med DHCP-klientens gränssnitts poster.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="d9c5d-184">Skillnaden mellan den här tjänsten och *nx_dhcp_set_interface_index* är att de senare bara anger ett enda gränssnitt för att köra DHCP, medan denna tjänst bara lägger till det angivna gränssnittet i listan över klient gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="d9c5d-185">Om du vill inaktivera ett gränssnitt för DHCP kan programmet anropa</span><span class="sxs-lookup"><span data-stu-id="d9c5d-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="d9c5d-186">*nx_dhcp_interface_disable* tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-187">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-187">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-188">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="d9c5d-189">**interface_index**: index för gränssnitt för att aktivera DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-190">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-190">Return Values</span></span>

- <span data-ttu-id="d9c5d-191">**NX_SUCCESS**: (0X00) slutförd DHCP-aktivering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="d9c5d-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0XA7) ingen post är tillgänglig för ett annat gränssnitt att aktive ras för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0XA3) gränssnitt aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-194">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-195">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-196">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-196">Allowed From</span></span>

<span data-ttu-id="d9c5d-197">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-198">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="d9c5d-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="d9c5d-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="d9c5d-200">Inaktivera det angivna gränssnittet för att köra DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="d9c5d-201">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-202">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-202">Description</span></span>

<span data-ttu-id="d9c5d-203">Den här tjänsten inaktiverar det angivna gränssnittet för att köra DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="d9c5d-204">Den initierar DHCP-klienten på det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="d9c5d-205">För att starta om DHCP-klienten måste programmet återaktivera gränssnittet med *nx_dhcp_interface_enable* och starta om DHCP genom att anropa *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-206">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-206">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-207">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="d9c5d-208">**interface_index**: index för gränssnitt att inaktivera DHCP på</span><span class="sxs-lookup"><span data-stu-id="d9c5d-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-209">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-209">Return Values</span></span>

- <span data-ttu-id="d9c5d-210">**NX_SUCCESS**: (0X00) lyckad DHCP-skapande</span><span class="sxs-lookup"><span data-stu-id="d9c5d-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="d9c5d-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-212">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-213">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d9c5d-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="d9c5d-214">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-215">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-215">Allowed From</span></span>

<span data-ttu-id="d9c5d-216">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-217">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="d9c5d-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="d9c5d-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="d9c5d-219">Ange DHCP-sändnings flagga</span><span class="sxs-lookup"><span data-stu-id="d9c5d-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-220">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="d9c5d-221">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-221">Description</span></span>

<span data-ttu-id="d9c5d-222">Den här tjänsten anger eller rensar sändnings flaggan för DHCP-meddelandets huvud för alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-223">För vissa DHCP-meddelanden (t. ex. identifiering) är sändnings flaggan inställd på sändning eftersom klienten inte har någon IP-adress.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="d9c5d-224">clear_flag värden:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-224">clear_flag values:</span></span> 

- <span data-ttu-id="d9c5d-225">**NX_TRUE**: sändnings flaggan är avmarkerad (begär unicast-svar)</span><span class="sxs-lookup"><span data-stu-id="d9c5d-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="d9c5d-226">**NX_FALSE**: sändnings flagga har angetts (begär sändnings svar)</span><span class="sxs-lookup"><span data-stu-id="d9c5d-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="d9c5d-227">Den här tjänsten är avsedd för DHCP-klienter som måste gå via en router för att komma till DHCP-servern, där routern avvisar broadcast-meddelanden vidarebefordras.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-228">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-228">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-229">**dhcp_ptr**: pekare till DHCP-kontroll block</span><span class="sxs-lookup"><span data-stu-id="d9c5d-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="d9c5d-230">**clear_flag**: värde att ange sändnings flaggan till</span><span class="sxs-lookup"><span data-stu-id="d9c5d-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-231">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-231">Return Values</span></span>

- <span data-ttu-id="d9c5d-232">**NX_SUCCESS**: (0X00) har ange flagga</span><span class="sxs-lookup"><span data-stu-id="d9c5d-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="d9c5d-233">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-234">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-234">Allowed From</span></span>

<span data-ttu-id="d9c5d-235">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-236">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="d9c5d-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="d9c5d-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="d9c5d-238">Ange eller rensa sändnings flaggan för det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-239">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="d9c5d-240">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-240">Description</span></span>

<span data-ttu-id="d9c5d-241">Den här tjänsten gör det möjligt för DHCP-klientens värd program att ange eller rensa sändnings flaggan i DHCP-klientens meddelanden till DHCP-servern på det angivna gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="d9c5d-242">Mer information finns i **nx_dhcp_clear_broadcast_flag**.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-243">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-243">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-244">**dhcp_ptr**: pekare till DHCP-kontroll block</span><span class="sxs-lookup"><span data-stu-id="d9c5d-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="d9c5d-245">**interface_index**: index för gränssnitt för att ange sändnings flaggan</span><span class="sxs-lookup"><span data-stu-id="d9c5d-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="d9c5d-246">**clear_flag**: värde att ange sändnings flaggan till</span><span class="sxs-lookup"><span data-stu-id="d9c5d-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-247">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-247">Return Values</span></span>

- <span data-ttu-id="d9c5d-248">**NX_SUCCESS**: (0X00) har ange flagga</span><span class="sxs-lookup"><span data-stu-id="d9c5d-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="d9c5d-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-250">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-251">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-252">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-252">Allowed From</span></span>

<span data-ttu-id="d9c5d-253">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-254">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="d9c5d-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="d9c5d-255">nx_dhcp_delete</span></span>

<span data-ttu-id="d9c5d-256">Ta bort en DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="d9c5d-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-257">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-258">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-258">Description</span></span>

<span data-ttu-id="d9c5d-259">Den här tjänsten tar bort en tidigare skapad DHCP-instans.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-260">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-260">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-261">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-262">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-262">Return Values</span></span>

- <span data-ttu-id="d9c5d-263">**NX_SUCCESS**: (0X00) DHCP-borttagning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="d9c5d-264">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-265">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-266">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-266">Allowed From</span></span>

<span data-ttu-id="d9c5d-267">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-268">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="d9c5d-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="d9c5d-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="d9c5d-270">Skicka ett meddelande om Force-förnyelse</span><span class="sxs-lookup"><span data-stu-id="d9c5d-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="d9c5d-271">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-272">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-272">Description</span></span>

<span data-ttu-id="d9c5d-273">Den här tjänsten gör det möjligt för värd programmet att skicka ett Force renew-meddelande på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-274">DHCP-klienten måste vara i ett begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="d9c5d-275">Den här funktionen ställer in statusen så att den FÖRNYAs så att DHCP-klienten kan försöka förnya innan T1-timeouten går ut.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="d9c5d-276">Om du vill skicka en tvingande förnyelse av ett speciellt gränssnitt när flera gränssnitt är DHCP-aktiverade använder du *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-277">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-277">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-278">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-279">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-279">Return Values</span></span>

- <span data-ttu-id="d9c5d-280">**NX_SUCCESS**: (0X00) har skickat framtvinga förnyelse.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="d9c5d-281">**NX_DHCP_NOT_BOUND**: KLIENTens IP-adress (0x94) är inte kopplad.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="d9c5d-282">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-283">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-284">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-284">Allowed From</span></span>

<span data-ttu-id="d9c5d-285">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-286">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="d9c5d-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="d9c5d-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="d9c5d-288">Skicka ett meddelande om Force-förnyelse på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-289">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-290">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-290">Description</span></span>

<span data-ttu-id="d9c5d-291">Den här tjänsten gör det möjligt för värd programmet att skicka ett Force renew-meddelande i Indataporten så länge gränssnittet har Aktiver ATS för DHCP (se *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="d9c5d-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="d9c5d-292">DHCP-klienten på det angivna gränssnittet måste vara i ett begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="d9c5d-293">Den här funktionen ställer in statusen så att den FÖRNYAs så att DHCP-klienten kan försöka förnya innan T1-timeouten går ut.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-294">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-294">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-295">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-296">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-296">Return Values</span></span>

- <span data-ttu-id="d9c5d-297">**NX_SUCCESS**: (0X00) har skickat framtvinga förnyelse.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="d9c5d-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-299">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-300">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-301">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-301">Allowed From</span></span>

<span data-ttu-id="d9c5d-302">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-303">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="d9c5d-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="d9c5d-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="d9c5d-305">Ange DHCP-klient paketets adresspool</span><span class="sxs-lookup"><span data-stu-id="d9c5d-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-306">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-307">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-307">Description</span></span>

<span data-ttu-id="d9c5d-308">Med den här tjänsten kan programmet skapa en DHCP-modempool genom att skicka en pekare till en tidigare skapad modempool i det här tjänst anropet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="d9c5d-309">Om du vill använda den här funktionen måste värd programmet definiera NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="d9c5d-310">När den har definierats skapas inte klientens modempool i *nx_dhcp_creates* tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="d9c5d-311">Programmet rekommenderas att använda standardvärden för DHCP-poolens paket nytto Last, definierad som NX_DHCP_PACKET_PAYLOAD i *nxd_dhcp_client. h* när du skapar poolen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-312">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-312">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-313">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="d9c5d-314">**packet_pool_ptr**: pekare till tidigare skapade paketets pool</span><span class="sxs-lookup"><span data-stu-id="d9c5d-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-315">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-315">Return Values</span></span>

- <span data-ttu-id="d9c5d-316">**NX_SUCCESS**: (0x00) DHCP-pool för DHCP-klient har angetts</span><span class="sxs-lookup"><span data-stu-id="d9c5d-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="d9c5d-317">**NX_NOT_ENABLED**: (0X14)-tjänsten är inte aktive rad</span><span class="sxs-lookup"><span data-stu-id="d9c5d-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="d9c5d-318">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) nytto lasten är för liten</span><span class="sxs-lookup"><span data-stu-id="d9c5d-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-320">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-320">Allowed From</span></span>

<span data-ttu-id="d9c5d-321">Program kod</span><span class="sxs-lookup"><span data-stu-id="d9c5d-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-322">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="d9c5d-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="d9c5d-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="d9c5d-324">Ange den begärda IP-adressen för DHCP-instansen</span><span class="sxs-lookup"><span data-stu-id="d9c5d-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-325">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="d9c5d-326">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-326">Description</span></span>

<span data-ttu-id="d9c5d-327">Den här tjänsten anger IP-adressen för DHCP-klienten som ska begäras från DHCP-servern på det första gränssnittet som är aktiverat för DHCP i DHCP-postposten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="d9c5d-328">Om *skip_discover_message* -flaggan har angetts hoppar DHCP-klienten över identifierings meddelandet och skickar ett meddelande om begäran.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="d9c5d-329">Om du vill ange en begäran för en speciell IP-adress för DHCP-meddelanden i ett gränssnitt använder du tjänsten *nx_dhcp_interface_request_client_ip* .</span><span class="sxs-lookup"><span data-stu-id="d9c5d-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-330">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-330">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-331">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="d9c5d-332">**client_ip_address**: IP-adress som ska begäras från DHCP-servern</span><span class="sxs-lookup"><span data-stu-id="d9c5d-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="d9c5d-333">**skip_discover_message**:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="d9c5d-334">Om värdet är true skickar DHCP-klienten begär ande meddelande</span><span class="sxs-lookup"><span data-stu-id="d9c5d-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="d9c5d-335">Om det här värdet är falskt skickas identifierings meddelandet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-336">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-336">Return Values</span></span>

- <span data-ttu-id="d9c5d-337">**NX_SUCCESS**: (0X00) BEGÄRd IP-adress har angetts.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="d9c5d-338">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP-adress begärdes</span><span class="sxs-lookup"><span data-stu-id="d9c5d-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-340">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-340">Allowed From</span></span>

<span data-ttu-id="d9c5d-341">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-342">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="d9c5d-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="d9c5d-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="d9c5d-344">Ange den begärda IP-adressen för DHCP-instansen på angivet gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-345">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="d9c5d-346">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-346">Description</span></span>

<span data-ttu-id="d9c5d-347">Den här tjänsten anger IP-adressen för DHCP-klienten som ska begäras från DHCP-servern på det angivna gränssnittet, om gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="d9c5d-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="d9c5d-348">Om *skip_discover_message* -flaggan har angetts hoppar DHCP-klienten över identifierings meddelandet och skickar ett meddelande om begäran.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-349">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-349">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-350">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="d9c5d-351">**Interface_index**: index för gränssnitt för att begära IP-adress på</span><span class="sxs-lookup"><span data-stu-id="d9c5d-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="d9c5d-352">**client_ip_address**: IP-adress som ska begäras från DHCP-servern</span><span class="sxs-lookup"><span data-stu-id="d9c5d-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="d9c5d-353">**skip_discover_message**: om värdet är true skickar DHCP-klienten begär ande meddelande. annars skickas identifierings meddelandet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-354">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-354">Return Values</span></span>

- <span data-ttu-id="d9c5d-355">**NX_SUCCESS**: (0X00) BEGÄRd IP-adress har angetts.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="d9c5d-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-357">NX_PTR_ERROR: (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-358">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-359">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-359">Allowed From</span></span>

<span data-ttu-id="d9c5d-360">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-361">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="d9c5d-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="d9c5d-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="d9c5d-363">Rensa nätverks parametrarna för DHCP-klienten</span><span class="sxs-lookup"><span data-stu-id="d9c5d-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="d9c5d-364">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-365">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-365">Description</span></span>

<span data-ttu-id="d9c5d-366">Den här tjänsten rensar nätverks parametrarna för värd programmet (IP-adress, nätverks adress och nätverks mask) och tar bort statusen för DHCP-klienten på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-367">Den används i kombination med *nx_dhcp_stop* och *nx_dhcp_start* att starta om DHCP-tillstånds datorn:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="d9c5d-368">Använd tjänsten *nx_dhcp_interface_reinitialize* om du vill initiera DHCP-klienten på ett speciellt gränssnitt när flera gränssnitt är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-369">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-369">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-370">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-371">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-371">Return Values</span></span>

- <span data-ttu-id="d9c5d-372">**NX_SUCCESS**: (0X00) DHCP har initierats om</span><span class="sxs-lookup"><span data-stu-id="d9c5d-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="d9c5d-373">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-374">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-374">Allowed From</span></span>

<span data-ttu-id="d9c5d-375">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-376">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="d9c5d-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="d9c5d-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="d9c5d-378">Rensa nätverks parametrarna för DHCP-klienten på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="d9c5d-379">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-380">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-380">Description</span></span>

<span data-ttu-id="d9c5d-381">Den här tjänsten rensar nätverks parametrarna (IP-adress, nätverks adress och nätverks mask) på det angivna gränssnittet om gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="d9c5d-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="d9c5d-382">Se *nx_dhcp_reinitialize* för mer information.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-383">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-383">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-384">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen</span><span class="sxs-lookup"><span data-stu-id="d9c5d-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="d9c5d-385">**interface_index**: index för gränssnittet att initiera om</span><span class="sxs-lookup"><span data-stu-id="d9c5d-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-386">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-386">Return Values</span></span>

- <span data-ttu-id="d9c5d-387">**NX_SUCCESS**: gränssnittet (0x00) har initierats om</span><span class="sxs-lookup"><span data-stu-id="d9c5d-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="d9c5d-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-389">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-390">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d9c5d-391">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-392">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-392">Allowed From</span></span>

<span data-ttu-id="d9c5d-393">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-394">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="d9c5d-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="d9c5d-395">nx_dhcp_release</span></span>

<span data-ttu-id="d9c5d-396">Frisläpp IP-adress för lån</span><span class="sxs-lookup"><span data-stu-id="d9c5d-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-397">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-398">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-398">Description</span></span>

<span data-ttu-id="d9c5d-399">Den här tjänsten frigör IP-adressen som hämtades från en DHCP-server genom att skicka RELEASE-meddelandet till den servern.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="d9c5d-400">Sedan initierar den om DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="d9c5d-401">Den här tjänsten används för alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="d9c5d-402">Programmet kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="d9c5d-403">Om du vill släppa en adress tillbaka till DHCP-servern i ett gränssnitt använder du tjänsten *nx_dhcp_interface_release*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-404">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-404">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-405">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-406">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-406">Return Values</span></span>

- <span data-ttu-id="d9c5d-407">**NX_SUCCESS**: (0X00) lyckad DHCP-version.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="d9c5d-408">**NX_DHCP_NOT_BOUND**: (0X94) IP-adressen har inte lånats ut så den kan inte släppas.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="d9c5d-409">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-410">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-411">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-411">Allowed From</span></span>

<span data-ttu-id="d9c5d-412">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-413">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="d9c5d-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="d9c5d-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="d9c5d-415">Frigör IP-adress på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-416">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-417">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-417">Description</span></span>

<span data-ttu-id="d9c5d-418">Den här tjänsten frigör IP-adressen som hämtades från en DHCP-server på det angivna gränssnittet och initierar om DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="d9c5d-419">Du kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-420">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-420">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-421">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-422">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-422">Return Values</span></span>

- <span data-ttu-id="d9c5d-423">**NX_SUCCESS**: (0X00) lyckad DHCP-version.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="d9c5d-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-425">**NX_DHCP_NOT_BOUND**: (0X94) IP-adressen har inte lånats ut så den kan inte släppas.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="d9c5d-426">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-427">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d9c5d-428">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-429">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-429">Allowed From</span></span>

<span data-ttu-id="d9c5d-430">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-431">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="d9c5d-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="d9c5d-432">nx_dhcp_decline</span></span>

<span data-ttu-id="d9c5d-433">Neka IP-adress från DHCP-server</span><span class="sxs-lookup"><span data-stu-id="d9c5d-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-434">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-435">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-435">Description</span></span>

<span data-ttu-id="d9c5d-436">Den här tjänsten avböjer en IP-adress som är lånad från DHCP-servern på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-437">Om NX_DHCP_CLIENT_ SEND_ ARP_PROBE har definierats skickar DHCP-klienten ett neka-meddelande om den identifierar att IP-adressen redan används.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="d9c5d-438">Se **ARP-avsökningar** i kapitel ett för mer information om konfiguration av ARP-avsökning i netx Duo DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="d9c5d-439">Programmet kan använda den här tjänsten för att neka sin IP-adress om den identifierar adressen används på annat sätt.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="d9c5d-440">Den här tjänsten initierar om DHCP-klienten så att den kan startas om genom att anropa *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-441">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-441">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-442">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-443">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-443">Return Values</span></span>

- <span data-ttu-id="d9c5d-444">**NX_SUCCESS**: (0X00) nekad har skickats</span><span class="sxs-lookup"><span data-stu-id="d9c5d-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="d9c5d-445">**NX_DHCP_NOT_BOUND**: (0X94) DHCP-klienten är inte kopplad</span><span class="sxs-lookup"><span data-stu-id="d9c5d-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="d9c5d-446">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-447">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d9c5d-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-448">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-448">Allowed From</span></span>

<span data-ttu-id="d9c5d-449">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-450">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="d9c5d-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="d9c5d-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="d9c5d-452">Neka IP-adress från DHCP-server på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-453">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-454">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-454">Description</span></span>

<span data-ttu-id="d9c5d-455">Den här tjänsten skickar meddelandet neka till servern för att neka en IP-adress som tilldelats av DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="d9c5d-456">Den initierar också om DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="d9c5d-457">Se *nx_dhcp_decline* för mer information.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-458">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-458">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-459">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-460">**Interface_index**: index för gränssnittet för att neka IP-adress</span><span class="sxs-lookup"><span data-stu-id="d9c5d-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-461">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-461">Return Values</span></span>

- <span data-ttu-id="d9c5d-462">**NX_SUCCESS**: (0X00) DHCP-neka meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="d9c5d-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="d9c5d-463">**NX_DHCP_NOT_BOUND**: (0X94) DHCP-klienten är inte kopplad</span><span class="sxs-lookup"><span data-stu-id="d9c5d-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="d9c5d-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-465">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-466">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d9c5d-467">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-468">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-468">Allowed From</span></span>

<span data-ttu-id="d9c5d-469">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-470">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="d9c5d-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="d9c5d-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="d9c5d-472">Skicka DHCP-meddelande till Server</span><span class="sxs-lookup"><span data-stu-id="d9c5d-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-473">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="d9c5d-474">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-474">Description</span></span>

<span data-ttu-id="d9c5d-475">Den här tjänsten skickar det angivna DHCP-meddelandet till DHCP-servern i det första gränssnitt som är aktiverat för DHCP som finns i DHCP-postposten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="d9c5d-476">Om du vill skicka en version eller avvisa ett meddelande måste programmet använda tjänsterna *nx_dhcp [_interface] _release*() eller *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="d9c5d-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="d9c5d-477">DHCP-klienten måste startas för att använda den här tjänsten, förutom för att skicka INFORM_REQUEST meddelande typen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="d9c5d-478">Den här tjänsten är inte avsedd för värd programmet till enhetens klient tillstånds dator.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-479">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-479">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-480">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="d9c5d-481">**dhcp_message_type**: meddelandebegäran (definieras i *nxd_dhcp_client. h*)</span><span class="sxs-lookup"><span data-stu-id="d9c5d-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-482">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-482">Return Values</span></span>

- <span data-ttu-id="d9c5d-483">**NX_SUCCESS**: (0X00) DHCP-meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="d9c5d-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="d9c5d-484">**NX_DHCP_NOT_STARTED**: (0X96) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="d9c5d-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="d9c5d-485">**NX_DHCP_INVALID_MESSAGE**: (0X9B) ogiltig meddelande typ som ska skickas</span><span class="sxs-lookup"><span data-stu-id="d9c5d-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="d9c5d-486">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-487">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-487">Allowed From</span></span>

<span data-ttu-id="d9c5d-488">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-489">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="d9c5d-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="d9c5d-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="d9c5d-491">Skicka DHCP-meddelande till server på ett speciellt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-492">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="d9c5d-493">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-493">Description</span></span>

<span data-ttu-id="d9c5d-494">Den här tjänsten skickar ett meddelande till DHCP-servern på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-495">Om du vill skicka en version eller avvisa ett meddelande måste programmet använda tjänsterna *nx_dhcp [_interface] _release*() eller *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="d9c5d-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="d9c5d-496">DHCP-klienten måste ha startats för att använda den här tjänsten, förutom för meddelande typen DHCP-meddelande begär Ande.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="d9c5d-497">Den här tjänsten är inte avsedd för värd programmet till enhetens klient tillstånds dator.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-498">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-498">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-499">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="d9c5d-500">**Interface_index**: index för gränssnitt att skicka meddelande på</span><span class="sxs-lookup"><span data-stu-id="d9c5d-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="d9c5d-501">**dhcp_message_type**: meddelandebegäran (definieras i nxd_dhcp_client. h)</span><span class="sxs-lookup"><span data-stu-id="d9c5d-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-502">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-502">Return Values</span></span>

- <span data-ttu-id="d9c5d-503">**NX_SUCCESS**: (0X00) DHCP-meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="d9c5d-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="d9c5d-504">**NX_DHCP_NOT_STARTED**: (0X96) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="d9c5d-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="d9c5d-505">**NX_DHCP_INVALID_MESSAGE**: (0X9B) ogiltig meddelande typ som ska skickas</span><span class="sxs-lookup"><span data-stu-id="d9c5d-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="d9c5d-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0XA4) gränssnitt är inte aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-507">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-508">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d9c5d-509">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-510">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-510">Allowed From</span></span>

<span data-ttu-id="d9c5d-511">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-512">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="d9c5d-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="d9c5d-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="d9c5d-514">Hämta DHCP-klientens DHCP-servers IP-adress</span><span class="sxs-lookup"><span data-stu-id="d9c5d-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-515">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="d9c5d-516">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-516">Description</span></span>

<span data-ttu-id="d9c5d-517">Den här tjänsten hämtar DHCP-klientens DHCP-servers IP-adress i det första gränssnittet som är aktiverat för DHCP som finns i DHCP-postposten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="d9c5d-518">Anroparen kan bara använda den här tjänsten när DHCP-klienten har bundits till en IP-adress som tilldelats av DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="d9c5d-519">Värd programmet kan använda tjänsten *nx_ip_status_check* för att kontrol lera att IP-adressen har angetts, eller så kan den använda nx-*_dhcp_state_change_notify* och fråga DHCP-klientens tillstånd NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="d9c5d-520">Mer information om hur du anger motringnings funktionen för tillstånds ändringar finns i *nx_dhcp_state_change_notify* .</span><span class="sxs-lookup"><span data-stu-id="d9c5d-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="d9c5d-521">Om du vill hitta DHCP-servern på ett speciellt gränssnitt när flera gränssnitt är aktiverade för DHCP-klienten, använder du tjänsten *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-522">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-522">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-523">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="d9c5d-524">**server_address**: pekare till SERVERNS IP-adress</span><span class="sxs-lookup"><span data-stu-id="d9c5d-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-525">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-525">Return Values</span></span>

- <span data-ttu-id="d9c5d-526">**NX_SUCCESS**: (0X00) DHCP-serveradress returnerades</span><span class="sxs-lookup"><span data-stu-id="d9c5d-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="d9c5d-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-528">NX_PTR_ERROR: (0x16) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="d9c5d-529">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-530">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-530">Allowed From</span></span>

<span data-ttu-id="d9c5d-531">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-532">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="d9c5d-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="d9c5d-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="d9c5d-534">Hämta DHCP-klientens DHCP-servers IP-adress på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-535">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="d9c5d-536">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-536">Description</span></span>

<span data-ttu-id="d9c5d-537">Den här tjänsten hämtar DHCP-klientens DHCP-servers IP-adress på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-538">DHCP-klienten måste vara i begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="d9c5d-539">När du har startat DHCP-klienten på det här gränssnittet kan värd programmet antingen använda *nx_ip_status_check* tjänsten för att kontrol lera att IP-adressen har angetts, eller så kan den använda DHCP-klientens tillstånd för att ändra motringning och fråga DHCP-klientens tillstånd att NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="d9c5d-540">Mer information om hur du anger motringnings funktionen för tillstånds ändringar finns i *nx_dhcp_state_change_notify* .</span><span class="sxs-lookup"><span data-stu-id="d9c5d-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-541">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-541">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-542">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="d9c5d-543">**Interface_index**: index för gränssnitt för att hämta IP-adress</span><span class="sxs-lookup"><span data-stu-id="d9c5d-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="d9c5d-544">**server_address**: pekare till SERVERNS IP-adress</span><span class="sxs-lookup"><span data-stu-id="d9c5d-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-545">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-545">Return Values</span></span>

- <span data-ttu-id="d9c5d-546">**NX_SUCCESS**: (0X00) DHCP-serveradress returnerades</span><span class="sxs-lookup"><span data-stu-id="d9c5d-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="d9c5d-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-548">**NX_DHCP_NOT_BOUND**: (0X94) DHCP-klienten är inte kopplad</span><span class="sxs-lookup"><span data-stu-id="d9c5d-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="d9c5d-549">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="d9c5d-550">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d9c5d-551">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-552">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-552">Allowed From</span></span>

<span data-ttu-id="d9c5d-553">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-554">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="d9c5d-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="d9c5d-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="d9c5d-556">Ange nätverks gränssnitt för DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="d9c5d-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-557">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-558">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-558">Description</span></span>

<span data-ttu-id="d9c5d-559">Den här tjänsten anger nätverks gränssnittet för DHCP-instansen att ansluta till DHCP-servern vid körning av DHCP-klienten som kon figurer ATS för ett enda nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="d9c5d-560">Som standard körs DHCP-klienten på det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="d9c5d-561">Om du vill köra DHCP på en sekundär tjänst använder du den här tjänsten för att ange det sekundära gränssnittet som DHCP-klient gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="d9c5d-562">Programmet måste tidigare registrera det angivna gränssnittet för IP-instansen med hjälp av tjänsten *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="d9c5d-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="d9c5d-563">Den här tjänsten är avsedd för program som endast avser att köra DHCP-klienten på ett gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="d9c5d-564">Om du vill köra DHCP på flera gränssnitt kan du se *nx_dhcp_interface_enable* för mer information.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-565">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-565">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-566">**dhcp_ptr**: pekar mot DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="d9c5d-567">**index**: index för enhetens nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-568">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-568">Return Values</span></span>

- <span data-ttu-id="d9c5d-569">**NX_SUCCESS**: gränssnittet (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="d9c5d-570">**NX_INVALID_INTERFACE**: (0X4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="d9c5d-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0XA3) gränssnitt aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0XA7) ingen post är tillgänglig för en annan</span><span class="sxs-lookup"><span data-stu-id="d9c5d-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="d9c5d-573">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="d9c5d-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-574">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-574">Allowed From</span></span>

<span data-ttu-id="d9c5d-575">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-576">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="d9c5d-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="d9c5d-577">nx_dhcp_start</span></span>

<span data-ttu-id="d9c5d-578">Starta DHCP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-579">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-580">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-580">Description</span></span>

<span data-ttu-id="d9c5d-581">Den här tjänsten startar DHCP-bearbetning på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-582">Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="d9c5d-583">Om du vill kontrol lera att IP-instansen är kopplad till en IP-adress i DHCP-klientens gränssnitt använder du *nx_ip_status_check* för att se bekräfta att IP-adressen är giltig.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="d9c5d-584">Om det finns andra gränssnitt som redan kör DHCP, kommer den här tjänsten inte att påverka dem.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="d9c5d-585">Använd tjänsten *nx_dhcp_interface_start* för att starta DHCP på ett speciellt gränssnitt när flera gränssnitt är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-586">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-586">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-587">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-588">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-588">Return Values</span></span>

- <span data-ttu-id="d9c5d-589">**NX_SUCCESS**: (0X00) lyckad DHCP-start.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="d9c5d-590">**NX_DHCP_ALREADY_STARTED**: (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="d9c5d-591">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-592">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-593">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-593">Allowed From</span></span>

<span data-ttu-id="d9c5d-594">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-595">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="d9c5d-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="d9c5d-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="d9c5d-597">Starta DHCP-bearbetning på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-598">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-599">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-599">Description</span></span>

<span data-ttu-id="d9c5d-600">Den här tjänsten startar DHCP-bearbetning på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-601">Se *nx_dhcp_interface_enable*() om du vill ha mer information om hur du aktiverar ett gränssnitt för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="d9c5d-602">Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="d9c5d-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="d9c5d-603">Om det inte finns några andra gränssnitt som kör DHCP-klienten, kommer tjänsten att starta/återuppta DHCP-klientens tråd och (åter) Aktivera DHCP-klientens timer.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="d9c5d-604">Programmet bör använda *nx_ip_status_check* för att kontrol lera om en IP-adress hämtas.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-605">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-605">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-606">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-607">**Interface_index**: indexet som DHCP-klienten ska startas</span><span class="sxs-lookup"><span data-stu-id="d9c5d-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-608">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-608">Return Values</span></span>

- <span data-ttu-id="d9c5d-609">**NX_SUCCESS**: (0X00) lyckad DHCP-start.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="d9c5d-610">**NX_DHCP_ALREADY_STARTED**: (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="d9c5d-611">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-612">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="d9c5d-613">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-614">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-614">Allowed From</span></span>

<span data-ttu-id="d9c5d-615">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-616">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="d9c5d-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="d9c5d-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="d9c5d-618">Ange funktion för att ändra motringning för DHCP-tillstånd</span><span class="sxs-lookup"><span data-stu-id="d9c5d-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-619">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="d9c5d-620">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-620">Description</span></span>

<span data-ttu-id="d9c5d-621">Den här tjänsten registrerar den angivna återanrops funktionen dhcp_state_change_notify för att meddela ett program om DHCP-tillstånds ändringar.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="d9c5d-622">Funktionen motringning tillhandahåller det tillstånd som DHCP-klienten har övergått till.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="d9c5d-623">Följande är värden som är associerade med de olika DHCP-tillstånden:</span><span class="sxs-lookup"><span data-stu-id="d9c5d-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="d9c5d-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="d9c5d-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="d9c5d-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="d9c5d-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="d9c5d-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="d9c5d-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="d9c5d-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="d9c5d-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="d9c5d-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="d9c5d-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="d9c5d-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="d9c5d-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="d9c5d-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="d9c5d-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="d9c5d-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="d9c5d-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="d9c5d-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="d9c5d-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-633">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-633">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-634">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-635">**dhcp_state_change_notify**: funktions pekare för motringning av tillstånds ändring</span><span class="sxs-lookup"><span data-stu-id="d9c5d-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-636">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-636">Return Values</span></span>

- <span data-ttu-id="d9c5d-637">**NX_SUCCESS**: (0X00) lyckades motringning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="d9c5d-638">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-639">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-640">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-640">Allowed From</span></span>

<span data-ttu-id="d9c5d-641">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-642">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="d9c5d-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="d9c5d-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="d9c5d-644">Ange funktionen motringning av DHCP-tillstånd i det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-645">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="d9c5d-646">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-646">Description</span></span>

<span data-ttu-id="d9c5d-647">Den här tjänsten registrerar den angivna callback-funktionen för att meddela ett program om DHCP-tillstånds ändringar.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="d9c5d-648">Funciton för motringning är gränssnitts index och det tillstånd som DHCP-klienten har övergått till på det gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="d9c5d-649">Mer information om tillstånds ändrings funktioner finns i *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="d9c5d-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-650">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-650">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-651">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-652">**dhcp_interface_state_change_notify**: funktions pekare för program återanrop</span><span class="sxs-lookup"><span data-stu-id="d9c5d-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-653">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-653">Return Values</span></span>

- <span data-ttu-id="d9c5d-654">**NX_SUCCESS**: (0X00) lyckades motringning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="d9c5d-655">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-656">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-656">Allowed From</span></span>

<span data-ttu-id="d9c5d-657">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="d9c5d-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-658">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="d9c5d-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="d9c5d-659">nx_dhcp_stop</span></span>

<span data-ttu-id="d9c5d-660">Stoppar DHCP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-661">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-662">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-662">Description</span></span>

<span data-ttu-id="d9c5d-663">Den här tjänsten stoppar DHCP-bearbetning på alla gränssnitt som har börjat DHCP-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="d9c5d-664">Om det inte finns några gränssnitt som bearbetar DHCP kommer den här tjänsten att pausa DHCP-klientens tråd och inaktivera DHCP-klientens timer.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="d9c5d-665">Använd tjänsten *nx_dhcp_interface_stop* för att stoppa DHCP på ett speciellt gränssnitt om flera gränssnitt är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-666">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-666">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-667">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-668">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-668">Return Values</span></span>

- <span data-ttu-id="d9c5d-669">**NX_SUCCESS**: (0X00) DHCP-stopp har slutförts</span><span class="sxs-lookup"><span data-stu-id="d9c5d-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="d9c5d-670">**NX_DHCP_NOT_STARTED**: (0X96) DHCP-instansen startades inte.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="d9c5d-671">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-672">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-673">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-673">Allowed From</span></span>

<span data-ttu-id="d9c5d-674">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-675">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="d9c5d-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="d9c5d-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="d9c5d-677">Stoppa DHCP-bearbetning på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-678">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d9c5d-679">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-679">Description</span></span>

<span data-ttu-id="d9c5d-680">Den här tjänsten stoppar DHCP-bearbetning på det angivna gränssnittet om DHCP redan har startats.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="d9c5d-681">Om det inte finns några andra gränssnitt som kör DHCP så pausas DHCP-tråden och timern.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-682">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-682">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-683">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-684">**Interface_index**: gränssnitt där DHCP-bearbetningen ska stoppas</span><span class="sxs-lookup"><span data-stu-id="d9c5d-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-685">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-685">Return Values</span></span>

- <span data-ttu-id="d9c5d-686">**NX_SUCCESS**: (0X00) DHCP-stopp har slutförts</span><span class="sxs-lookup"><span data-stu-id="d9c5d-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="d9c5d-687">**NX_DHCP_NOT_STARTED**: (0X96) DHCP har inte startats.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="d9c5d-688">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-689">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="d9c5d-690">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-691">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-691">Allowed From</span></span>

<span data-ttu-id="d9c5d-692">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-693">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="d9c5d-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="d9c5d-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="d9c5d-695">Hämta ett DHCP-alternativ från senaste Server svar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-696">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="d9c5d-697">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-697">Description</span></span>

<span data-ttu-id="d9c5d-698">Den här tjänsten hämtar det angivna DHCP-alternativet från bufferten för DHCP-alternativ i det första gränssnitt som är aktiverat för DHCP som finns på DHCP-klienttjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="d9c5d-699">Om det lyckas kopieras alternativ data till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-700">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-700">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-701">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="d9c5d-702">**request_option**: DHCP-alternativet som anges i RFC: erna.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="d9c5d-703">Se alternativet NX_DHCP_OPTION i *nxd_dhcp_client. h*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="d9c5d-704">**destination_ptr**: pekar mot målet för svars strängen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="d9c5d-705">**destination_size**: pekar mot målets storlek och vid retur, målet att placera antalet byte som returneras.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-706">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-706">Return Values</span></span>

- <span data-ttu-id="d9c5d-707">**NX_SUCCESS**: (0X00) lyckad alternativ hämtning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="d9c5d-708">**NX_DHCP_NOT_BOUND**: (0X94) DHCP-klienten är inte kopplad.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="d9c5d-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="d9c5d-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="d9c5d-710">**NX_DHCP_DEST_TO_SMALL**: (0X95) destinationen är för liten för att rymma svar.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="d9c5d-711">**NX_DHCP_PARSE_ERROR**: alternativet (0x97) hittades inte i Server svaret.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="d9c5d-712">NX_PTR_ERROR: (0x16) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="d9c5d-713">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-714">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-714">Allowed From</span></span>

<span data-ttu-id="d9c5d-715">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-716">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="d9c5d-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="d9c5d-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="d9c5d-718">Hämta ett DHCP-alternativ från senaste Server svar på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="d9c5d-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-719">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="d9c5d-720">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-720">Description</span></span>

<span data-ttu-id="d9c5d-721">Den här tjänsten hämtar det angivna DHCP-alternativet från bufferten för DHCP-alternativ på det angivna gränssnittet, om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="d9c5d-722">Om det lyckas kopieras alternativ data till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-723">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-723">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-724">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-725">**Interface_index**: indexet som det angivna alternativet ska hämtas till</span><span class="sxs-lookup"><span data-stu-id="d9c5d-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="d9c5d-726">**request_option**: DHCP-alternativet som anges i RFC: erna.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="d9c5d-727">Se NX_DHCP_OPTION alternativ: i *nxd_dhcp_client. h*.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="d9c5d-728">**destination_ptr**: pekar mot målet för svars strängen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="d9c5d-729">**destination_size**: pekar mot målets storlek och vid retur, målet att placera antalet byte som returneras.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-730">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-730">Return Values</span></span>

- <span data-ttu-id="d9c5d-731">**NX_SUCCESS**: (0X00) lyckad alternativ hämtning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="d9c5d-732">**NX_DHCP_NOT_BOUND**: (0X94) IP-adress inte tilldelad</span><span class="sxs-lookup"><span data-stu-id="d9c5d-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="d9c5d-733">**NX_DHCP_DEST_TO_SMALL**: (0X95) bufferten är för liten</span><span class="sxs-lookup"><span data-stu-id="d9c5d-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="d9c5d-734">**NX_DHCP_PARSE_ERROR**: DHCP-alternativet (0x97) hittades inte i Server svaret.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="d9c5d-735">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d9c5d-736">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="d9c5d-737">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="d9c5d-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-738">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-738">Allowed From</span></span>

<span data-ttu-id="d9c5d-739">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-740">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="d9c5d-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="d9c5d-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="d9c5d-742">Konvertera fyra byte till ULONG</span><span class="sxs-lookup"><span data-stu-id="d9c5d-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-743">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="d9c5d-744">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-744">Description</span></span>

<span data-ttu-id="d9c5d-745">Den här tjänsten konverterar de fyra tecknen till "option_string_ptr" till ett osignerat långt värde.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="d9c5d-746">Det är särskilt användbart när IP-adresser är</span><span class="sxs-lookup"><span data-stu-id="d9c5d-746">It is especially useful when IP addresses are</span></span>  
<span data-ttu-id="d9c5d-747">finner.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-747">present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-748">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-748">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-749">**option_string_ptr**: pekare till tidigare hämtade alternativ sträng.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-750">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-750">Return Values</span></span>

- <span data-ttu-id="d9c5d-751">**Värde**: värdet för de första fyra byten.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-752">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-752">Allowed From</span></span>

<span data-ttu-id="d9c5d-753">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-754">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="d9c5d-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="d9c5d-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="d9c5d-756">Ange callback-funktionen för att lägga till användar alternativ som har angetts</span><span class="sxs-lookup"><span data-stu-id="d9c5d-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="d9c5d-757">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d9c5d-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="d9c5d-758">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d9c5d-758">Description</span></span>

<span data-ttu-id="d9c5d-759">Den här tjänsten registrerar den angivna callback-funktionen för att lägga till användar alternativ.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="d9c5d-760">Om funktionen motringning har angetts kan programmen lägga till användar alternativ i paketet genom iface_index och message_type.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="d9c5d-761">I användarens rutin.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-761">In user’s routine.</span></span> <span data-ttu-id="d9c5d-762">Program måste följa alternativen för DHCP-alternativ när du lägger till användar alternativ.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="d9c5d-763">Den totala storleken för användar alternativ måste vara mindre än eller lika med user_option_length och uppdatera user_option_length som en verklig längd.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="d9c5d-764">Returnera NX_TRUE om alternativet har lagts till, annars returnerar NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d9c5d-765">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d9c5d-765">Input Parameters</span></span>

- <span data-ttu-id="d9c5d-766">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="d9c5d-767">**dhcp_user_option_add**: pekare till användar alternativ Lägg till funktion.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="d9c5d-768">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d9c5d-768">Return Values</span></span>

- <span data-ttu-id="d9c5d-769">**NX_SUCCESS**: (0X00) lyckades motringning.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="d9c5d-770">NX_PTR_ERROR: (0x16) ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="d9c5d-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d9c5d-771">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d9c5d-771">Allowed From</span></span>

<span data-ttu-id="d9c5d-772">Konversation</span><span class="sxs-lookup"><span data-stu-id="d9c5d-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d9c5d-773">Exempel</span><span class="sxs-lookup"><span data-stu-id="d9c5d-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

