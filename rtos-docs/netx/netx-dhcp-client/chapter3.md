---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DHCP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826796"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="28766-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP Client Services</span><span class="sxs-lookup"><span data-stu-id="28766-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="28766-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DHCP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="28766-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="28766-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="28766-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="28766-106">**nx_dhcp_create**: *skapa en DHCP-instans*</span><span class="sxs-lookup"><span data-stu-id="28766-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="28766-107">**nx_dhcp_clear_broadcast_flag**: Rensa sändnings flagga på klient meddelanden</span><span class="sxs-lookup"><span data-stu-id="28766-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="28766-108">**nx_dhcp_delete**: *ta bort en DHCP-instans*</span><span class="sxs-lookup"><span data-stu-id="28766-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="28766-109">**nx_dhcp_decline**: skicka *neka meddelande till Server*</span><span class="sxs-lookup"><span data-stu-id="28766-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="28766-110">**nx_dhcp_force_renew**: *Skicka framtvinga förnyelse av meddelande*</span><span class="sxs-lookup"><span data-stu-id="28766-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="28766-111">**nx_dhcp_packet_pool_set**: *ange DHCP-klient paketets adresspool*</span><span class="sxs-lookup"><span data-stu-id="28766-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="28766-112">**nx_dhcp_release**: Skicka ett *release-meddelande till servern*</span><span class="sxs-lookup"><span data-stu-id="28766-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="28766-113">**nx_dhcp_reinitialize**: *ta bort nätverks parametrar för DHCP-klienter*</span><span class="sxs-lookup"><span data-stu-id="28766-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="28766-114">**nx_dhcp_request_client_ip**: *Ange en speciell IP-adress*</span><span class="sxs-lookup"><span data-stu-id="28766-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="28766-115">**nx_dhcp_send_request**: *Skicka DHCP-meddelande till Server*</span><span class="sxs-lookup"><span data-stu-id="28766-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="28766-116">**nx_dhcp_server_address_get**: *Hämta DHCP-klientens DHCP-serveradress*</span><span class="sxs-lookup"><span data-stu-id="28766-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="28766-117">**nx_dhcp_set_interface_index**: *Ange klient nätverks gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="28766-118">**nx_dhcp_start**: *Starta DHCP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="28766-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="28766-119">**nx_dhcp_state_change_notify**: *meddela programmet om ändring av DHCP-tillstånd*</span><span class="sxs-lookup"><span data-stu-id="28766-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="28766-120">**nx_dhcp_stop**: *stoppa DHCP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="28766-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="28766-121">**nx_dhcp_user_option_retrieve**: *Hämta DHCP-alternativ*</span><span class="sxs-lookup"><span data-stu-id="28766-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="28766-122">**nx_dhcp_user_option_convert**: *konvertera fyra byte till ulong*</span><span class="sxs-lookup"><span data-stu-id="28766-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="28766-123">Gränssnitt för vissa DHCP-klient tjänster:</span><span class="sxs-lookup"><span data-stu-id="28766-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="28766-124">**nx_dhcp_interface_clear_broadcast_flag**: *Rensa sändnings flagga på klient meddelanden i angivet gränssnitt*</span><span class="sxs-lookup"><span data-stu-id="28766-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="28766-125">**nx_dhcp_interface_enable**: *Aktivera gränssnitt för att köra DHCP på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="28766-126">**nx_dhcp_interface_disable**: *inaktivera gränssnittet för att köra DHCP på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="28766-127">**nx_dhcp_interface_decline**: *Skicka neka meddelande till server på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="28766-128">**nx_dhcp_interface_force_renew**: *Skicka ett Force renew-meddelande på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="28766-129">**nx_dhcp_interface_reinitialize**: *ta bort nätverks parametrar för DHCP-klienter på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="28766-130">**nx_dhcp_interface_release**: *Skicka ett release-meddelande till servern på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="28766-131">**nx_dhcp_interface_request_client_ip**: *Ange en specifik IP-adress för det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="28766-132">**nx_dhcp_interface_send_request**: *Skicka DHCP-meddelande till servern på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="28766-133">**nx_dhcp_interface_server_address_get**: *Hämta IP-adressen för DHCP-servern på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="28766-134">**nx_dhcp_interface_start**: *Starta DHCP-klient bearbetningen på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="28766-135">**nx_dhcp_interface_stop**: *stoppa DHCP-klientens bearbetning på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="28766-136">**nx_dhcp_interface_state_change_notify**: *Ange callback-funktionen när DHCP-tillstånd ändras på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="28766-137">**nx_dhcp_interface_user_option_retrieve**: *Hämta det angivna DHCP-alternativet på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="28766-138">DHCP-klienttjänster om NX_DHCP_CLIENT_RESORE_STATE definieras:</span><span class="sxs-lookup"><span data-stu-id="28766-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="28766-139">**nx_dhcp_resume**: *återuppta tidigare upprättat DHCP-klient tillstånd*</span><span class="sxs-lookup"><span data-stu-id="28766-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="28766-140">**nx_dhcp_suspend**: *pausa bearbetningen av DHCP-klientens tillstånd*</span><span class="sxs-lookup"><span data-stu-id="28766-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="28766-141">**nx_dhcp_client_get_record**: *skapa en post för DHCP-klientens tillstånd*</span><span class="sxs-lookup"><span data-stu-id="28766-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="28766-142">**nx_dhcp_client_restore_record**: *återställa en tidigare sparad post till DHCP-klienten*</span><span class="sxs-lookup"><span data-stu-id="28766-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="28766-143">**nx_dhcp_client_update_time_remaining**: *Uppdatera tiden som återstår i det aktuella DHCP-läget*</span><span class="sxs-lookup"><span data-stu-id="28766-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="28766-144">Gränssnitt för klient tjänster för DHCP om NX_DHCP_CLIENT_RESORE_STATE definieras:</span><span class="sxs-lookup"><span data-stu-id="28766-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="28766-145">**nx_dhcp_client_interface_get_record**: *skapa en post av DHCP-klientens tillstånd på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="28766-146">**nx_dhcp_client_interface_restore_record**: *Återställ en tidigare sparad post till DHCP-klienten på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="28766-147">**nx_dhcp_client_interface_update_time_remaining**: *Uppdatera tiden som återstår i det aktuella DHCP-läget på det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="28766-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="28766-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="28766-148">nx_dhcp_create</span></span>

<span data-ttu-id="28766-149">Skapa en DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="28766-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-150">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-151">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-151">Description</span></span>

<span data-ttu-id="28766-152">Den här tjänsten skapar en DHCP-instans för den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="28766-153">Som standard är det primära gränssnittet aktiverat för att köra DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="28766-154">Inmatade namn, men som inte används i NetX-implementeringen av DHCP-klienten, måste följa RFC 1035-kriterier för värdnamn.</span><span class="sxs-lookup"><span data-stu-id="28766-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="28766-155">Den totala längden får inte överskrida 255 tecken, etiketter åtskilda av punkter måste börja med en bokstav och sluta med en bokstav eller siffra och får innehålla bindestreck, men inte andra icke-alfanumeriska tecken.</span><span class="sxs-lookup"><span data-stu-id="28766-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="28766-156">Om programmet vill köra ett annat gränssnitt som registrerats med IP-instansen (med *nx_ip_interface_attach*) kan programmet anropa *nx_dhcp_set_interface_index* för att köra DHCP på bara det gränssnittet, eller *nx_dhcp_interface_enable* för att köra DHCP på det gränssnittet också.</span><span class="sxs-lookup"><span data-stu-id="28766-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="28766-157">Mer information finns i Beskrivning av dessa tjänster.</span><span class="sxs-lookup"><span data-stu-id="28766-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="28766-158">Programmet måste se till att nytto lasten i DHCP-adresspoolen har stöd för den minsta storleken för DHCP-meddelanden som anges i RFC 2131 avsnitt 2 (548 byte av DHCP-meddelande data samt UDP, IP och fysiska nätverks ram rubriker).</span><span class="sxs-lookup"><span data-stu-id="28766-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-159">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-159">Input Parameters</span></span>

- <span data-ttu-id="28766-160">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="28766-161">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="28766-162">**name_ptr** Pekare till värd namnet för DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-163">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-163">Return Values</span></span>

- <span data-ttu-id="28766-164">**NX_SUCCESS** (0X00) DHCP-skapande har slutförts</span><span class="sxs-lookup"><span data-stu-id="28766-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="28766-165">**NX_DHCP_INVALID_NAME** (0XA8) ogiltigt värdnamn</span><span class="sxs-lookup"><span data-stu-id="28766-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="28766-166">**NX_DHCP_INVALID_PAYLOAD** (0X9C) nytto lasten är för liten för DHCP-meddelande</span><span class="sxs-lookup"><span data-stu-id="28766-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="28766-167">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-168">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-168">Allowed From</span></span>

<span data-ttu-id="28766-169">**Trådar,** Initialisering</span><span class="sxs-lookup"><span data-stu-id="28766-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="28766-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="28766-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="28766-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="28766-172">Aktivera det angivna gränssnittet för att köra DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="28766-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-174">Description</span></span>

<span data-ttu-id="28766-175">Den här tjänsten aktiverar det angivna gränssnittet för att köra DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="28766-176">Som standard är det primära gränssnittet aktiverat för DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="28766-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="28766-177">I det här läget kan du starta DHCP på det här gränssnittet antingen genom att anropa *nx_dhcp_interface_start* eller starta DHCP på alla aktiverade gränssnitt *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="28766-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="28766-178">Obs! programmet måste först registrera det här gränssnittet med IP-instansen med hjälp av *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="28766-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="28766-179">Vidare måste det finnas ett tillgängligt DHCP-klient gränssnitt för att lägga till det här gränssnittet i listan över aktiverade gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="28766-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="28766-180">Som standard har NX_DHCP_CLIENT_MAX_RECORDS definierats till 1.</span><span class="sxs-lookup"><span data-stu-id="28766-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="28766-181">Ange det här alternativet till det maximala antalet gränssnitt som förväntas köra DHCP-klienten samtidigt.</span><span class="sxs-lookup"><span data-stu-id="28766-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="28766-182">Vanligt vis är NX_DHCP_CLIENT_MAX_RECORDS samma NX_MAX_PHYSICAL_INTERFACES; men om en enhet har fler fysiska gränssnitt än det förväntar sig att köra DHCP-klienten, kan du spara minne genom att ange NX_DHCP_CLIENT_MAX_RECORDS till mindre än det numret.</span><span class="sxs-lookup"><span data-stu-id="28766-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="28766-183">Det finns inte någon till en mappning av fysiska gränssnitt med DHCP-klientens gränssnitts poster.</span><span class="sxs-lookup"><span data-stu-id="28766-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="28766-184">Skillnaden mellan den här tjänsten och *nx_dhcp_set_interface_index* är att de senare bara anger ett enda gränssnitt för att köra DHCP, medan denna tjänst bara lägger till det angivna gränssnittet i listan över klient gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="28766-185">Om du vill inaktivera ett gränssnitt för DHCP kan programmet anropa tjänsten *nx_dhcp_interface_disable* .</span><span class="sxs-lookup"><span data-stu-id="28766-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-186">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-186">Input Parameters</span></span>

- <span data-ttu-id="28766-187">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="28766-188">**interface_index** Index för gränssnitt för att aktivera DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-189">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-189">Return Values</span></span>

- <span data-ttu-id="28766-190">**NX_SUCCESS** (0X00) genomförde DHCP-aktivering</span><span class="sxs-lookup"><span data-stu-id="28766-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="28766-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) ingen post är tillgänglig för ett annat gränssnitt att aktive ras för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="28766-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** -gränssnitt (0xA3) aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="28766-193">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-194">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-195">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-195">Allowed From</span></span>

<span data-ttu-id="28766-196">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="28766-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="28766-197">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="28766-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="28766-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="28766-199">Inaktivera det angivna gränssnittet för att köra DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="28766-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-201">Description</span></span>

<span data-ttu-id="28766-202">Den här tjänsten inaktiverar det angivna gränssnittet för att köra DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="28766-203">Den initierar DHCP-klienten på det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="28766-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="28766-204">För att starta om DHCP-klienten måste programmet återaktivera gränssnittet med *nx_dhcp_interface_enable* och starta om DHCP genom att anropa *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="28766-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-205">Input Parameters</span></span>

- <span data-ttu-id="28766-206">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="28766-207">**interface_index** Index för gränssnitt att inaktivera DHCP på</span><span class="sxs-lookup"><span data-stu-id="28766-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-208">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-208">Return Values</span></span>

- <span data-ttu-id="28766-209">**NX_SUCCESS** (0X00) DHCP-skapande har slutförts</span><span class="sxs-lookup"><span data-stu-id="28766-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="28766-210">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-211">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-212">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="28766-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="28766-213">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-214">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-214">Allowed From</span></span>

<span data-ttu-id="28766-215">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-216">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="28766-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="28766-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="28766-218">Ange DHCP-sändnings flagga</span><span class="sxs-lookup"><span data-stu-id="28766-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-219">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="28766-220">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-220">Description</span></span>

<span data-ttu-id="28766-221">Den här tjänsten anger eller rensar sändnings flaggan för DHCP-meddelandets huvud för alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="28766-222">För vissa DHCP-meddelanden (t. ex. identifiering) är sändnings flaggan inställd på sändning eftersom klienten inte har någon IP-adress.</span><span class="sxs-lookup"><span data-stu-id="28766-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="28766-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="28766-223">__clear_flag__</span></span>


- <span data-ttu-id="28766-224">Flaggan för **NX_TRUE** sändning rensas (begär unicast-svar)</span><span class="sxs-lookup"><span data-stu-id="28766-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="28766-225">**NX_FALSE** broadcast-flaggan har angetts (begär sändnings svar)</span><span class="sxs-lookup"><span data-stu-id="28766-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="28766-226">Den här tjänsten är avsedd för DHCP-klienter som måste gå via en router för att komma till DHCP-servern, där routern avvisar broadcast-meddelanden vidarebefordras.</span><span class="sxs-lookup"><span data-stu-id="28766-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-227">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-227">Input Parameters</span></span>

- <span data-ttu-id="28766-228">**dhcp_ptr** Pekare till DHCP-kontroll block</span><span class="sxs-lookup"><span data-stu-id="28766-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="28766-229">**clear_flag** Värde att ange sändnings flaggan till</span><span class="sxs-lookup"><span data-stu-id="28766-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-230">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-230">Return Values</span></span>

- <span data-ttu-id="28766-231">**NX_SUCCESS** (0X00) har uppdaterat sändnings flaggan</span><span class="sxs-lookup"><span data-stu-id="28766-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="28766-232">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-233">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="28766-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-234">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-234">Allowed From</span></span>

<span data-ttu-id="28766-235">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="28766-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="28766-236">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="28766-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="28766-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="28766-238">Ange eller rensa sändnings flaggan för det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-239">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="28766-240">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-240">Description</span></span>

<span data-ttu-id="28766-241">Den här tjänsten gör det möjligt för DHCP-klientens värd program att ange eller rensa sändnings flaggan i DHCP-klientens meddelanden till DHCP-servern på det angivna gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="28766-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="28766-242">Mer information finns i **nx_dhcp_clear_broadcast_flag**</span><span class="sxs-lookup"><span data-stu-id="28766-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-243">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-243">Input Parameters</span></span>

- <span data-ttu-id="28766-244">**dhcp_ptr** Pekare till DHCP-kontroll block</span><span class="sxs-lookup"><span data-stu-id="28766-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="28766-245">**interface_index** Index för gränssnitt för att ange sändnings flagga</span><span class="sxs-lookup"><span data-stu-id="28766-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="28766-246">**clear_flag** Värde att ange sändnings flaggan till</span><span class="sxs-lookup"><span data-stu-id="28766-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-247">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-247">Return Values</span></span>

- <span data-ttu-id="28766-248">**NX_SUCCESS** (0X00) har uppdaterat sändnings flaggan</span><span class="sxs-lookup"><span data-stu-id="28766-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="28766-249">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-250">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-251">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-252">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-252">Allowed From</span></span>

<span data-ttu-id="28766-253">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="28766-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="28766-254">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="28766-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="28766-255">nx_dhcp_delete</span></span>

<span data-ttu-id="28766-256">Ta bort en DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="28766-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-257">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-258">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-258">Description</span></span>

<span data-ttu-id="28766-259">Den här tjänsten tar bort en tidigare skapad DHCP-instans.</span><span class="sxs-lookup"><span data-stu-id="28766-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-260">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-260">Input Parameters</span></span>

- <span data-ttu-id="28766-261">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-262">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-262">Return Values</span></span>

- <span data-ttu-id="28766-263">**NX_SUCCESS** (0X00) DHCP-borttagning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="28766-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="28766-264">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-265">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-266">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-266">Allowed From</span></span>

<span data-ttu-id="28766-267">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-268">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="28766-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="28766-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="28766-270">Skicka ett meddelande om Force-förnyelse</span><span class="sxs-lookup"><span data-stu-id="28766-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="28766-271">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-272">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-272">Description</span></span>

<span data-ttu-id="28766-273">Den här tjänsten gör det möjligt för värd programmet att skicka ett Force renew-meddelande på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="28766-274">DHCP-klienten måste vara i ett begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="28766-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="28766-275">Den här funktionen ställer in statusen så att den FÖRNYAs så att DHCP-klienten kan försöka förnya innan T1-timeouten går ut.</span><span class="sxs-lookup"><span data-stu-id="28766-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="28766-276">Om du vill skicka en tvingande förnyelse av ett speciellt gränssnitt när flera gränssnitt är DHCP-aktiverade använder du *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="28766-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-277">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-277">Input Parameters</span></span>

- <span data-ttu-id="28766-278">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-279">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-279">Return Values</span></span>

- <span data-ttu-id="28766-280">**NX_SUCCESS** (0X00) har skickat en framtvinga förnyelse.</span><span class="sxs-lookup"><span data-stu-id="28766-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="28766-281">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-282">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-283">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-283">Allowed From</span></span>

<span data-ttu-id="28766-284">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-285">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="28766-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="28766-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="28766-287">Skicka ett meddelande om Force-förnyelse på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-288">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-289">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-289">Description</span></span>

<span data-ttu-id="28766-290">Den här tjänsten gör det möjligt för värd programmet att skicka ett Force renew-meddelande i Indataporten så länge gränssnittet har Aktiver ATS för DHCP (se *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="28766-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="28766-291">DHCP-klienten på det angivna gränssnittet måste vara i ett begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="28766-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="28766-292">Den här funktionen ställer in statusen så att den FÖRNYAs så att DHCP-klienten kan försöka förnya innan T1-timeouten går ut.</span><span class="sxs-lookup"><span data-stu-id="28766-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-293">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-293">Input Parameters</span></span>

- <span data-ttu-id="28766-294">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-295">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-295">Return Values</span></span>

- <span data-ttu-id="28766-296">**NX_SUCCESS** (0X00) har skickat en framtvinga förnyelse.</span><span class="sxs-lookup"><span data-stu-id="28766-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="28766-297">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-298">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-299">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-300">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-300">Allowed From</span></span>

<span data-ttu-id="28766-301">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-302">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="28766-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="28766-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="28766-304">Ange DHCP-klient paketets adresspool</span><span class="sxs-lookup"><span data-stu-id="28766-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-305">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-306">Description</span></span>

<span data-ttu-id="28766-307">Med den här tjänsten kan programmet skapa en DHCP-modempool genom att skicka en pekare till en tidigare skapad modempool i det här tjänst anropet.</span><span class="sxs-lookup"><span data-stu-id="28766-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="28766-308">Om du vill använda den här funktionen måste värd programmet definiera NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="28766-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="28766-309">När den har definierats skapas inte klientens modempool i *nx_dhcp_creates* tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="28766-310">Observera att programmet rekommenderas att använda standardvärden för DHCP-poolens paket nytto Last, definierad som NX_DHCP_PACKET_PAYLOAD i *nx_dhcp. h* när du skapar poolen.</span><span class="sxs-lookup"><span data-stu-id="28766-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-311">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-311">Input Parameters</span></span>

- <span data-ttu-id="28766-312">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="28766-313">**packet_pool_ptr** Pekare till tidigare skapade paket pool</span><span class="sxs-lookup"><span data-stu-id="28766-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-314">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-314">Return Values</span></span>

- <span data-ttu-id="28766-315">**NX_SUCCESS** (0x00) DHCP-pool för DHCP-klient har angetts</span><span class="sxs-lookup"><span data-stu-id="28766-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="28766-316">Tjänsten **NX_NOT_ENABLED** (0x14) är inte aktive rad</span><span class="sxs-lookup"><span data-stu-id="28766-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="28766-317">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-318">NX_DHCP_INVALID_PAYLOAD (0x9C) nytto lasten är för liten</span><span class="sxs-lookup"><span data-stu-id="28766-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-319">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-319">Allowed From</span></span>

<span data-ttu-id="28766-320">Program kod</span><span class="sxs-lookup"><span data-stu-id="28766-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="28766-321">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="28766-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="28766-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="28766-323">Ange den begärda IP-adressen för DHCP-instansen</span><span class="sxs-lookup"><span data-stu-id="28766-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-324">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="28766-325">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-325">Description</span></span>

<span data-ttu-id="28766-326">Den här tjänsten anger IP-adressen för DHCP-klienten som ska begäras från DHCP-servern på det första gränssnittet som är aktiverat för DHCP i DHCP-postposten.</span><span class="sxs-lookup"><span data-stu-id="28766-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="28766-327">Om *skip_discover_message* -flaggan har angetts hoppar DHCP-klienten över identifierings meddelandet och skickar ett meddelande om begäran.</span><span class="sxs-lookup"><span data-stu-id="28766-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="28766-328">Om du vill ange en begäran för en speciell IP-adress för DHCP-meddelanden i ett gränssnitt använder du tjänsten *nx_dhcp_interface_request_client_ip* .</span><span class="sxs-lookup"><span data-stu-id="28766-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-329">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-329">Input Parameters</span></span>

- <span data-ttu-id="28766-330">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="28766-331">**client_ip_address** IP-adress att begära från DHCP-server</span><span class="sxs-lookup"><span data-stu-id="28766-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="28766-332">**skip_discover_message** Om värdet är true skickar DHCP-klienten begär ande meddelande</span><span class="sxs-lookup"><span data-stu-id="28766-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="28766-333">Om det här värdet är falskt skickas identifierings meddelandet.</span><span class="sxs-lookup"><span data-stu-id="28766-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-334">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-334">Return Values</span></span>

- <span data-ttu-id="28766-335">Den begärda IP-adressen för **NX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="28766-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="28766-336">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-337">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-338">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="28766-339">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-339">Allowed From</span></span>

<span data-ttu-id="28766-340">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-341">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="28766-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="28766-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="28766-343">Ange den begärda IP-adressen för DHCP-instansen på angivet gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-344">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="28766-345">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-345">Description</span></span>

<span data-ttu-id="28766-346">Den här tjänsten anger IP-adressen för DHCP-klienten som ska begäras från DHCP-servern på det angivna gränssnittet, om gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="28766-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="28766-347">Om *skip_discover_message* -flaggan har angetts hoppar DHCP-klienten över identifierings meddelandet och skickar ett meddelande om begäran.</span><span class="sxs-lookup"><span data-stu-id="28766-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-348">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-348">Input Parameters</span></span>

- <span data-ttu-id="28766-349">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="28766-350">**Interface_index** Index för gränssnitt att begära IP-adress på</span><span class="sxs-lookup"><span data-stu-id="28766-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="28766-351">**client_ip_address** IP-adress att begära från DHCP-server</span><span class="sxs-lookup"><span data-stu-id="28766-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="28766-352">**skip_discover_message** Om värdet är true skickar DHCP-klienten begär ande meddelande. annars skickas identifierings meddelandet.</span><span class="sxs-lookup"><span data-stu-id="28766-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-353">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-353">Return Values</span></span>

- <span data-ttu-id="28766-354">Den begärda IP-adressen för **NX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="28766-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="28766-355">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-356">NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="28766-357">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="28766-358">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-358">Allowed From</span></span>

<span data-ttu-id="28766-359">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-360">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="28766-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="28766-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="28766-362">Rensa nätverks parametrarna för DHCP-klienten</span><span class="sxs-lookup"><span data-stu-id="28766-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="28766-363">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-364">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-364">Description</span></span>

<span data-ttu-id="28766-365">Den här tjänsten rensar nätverks parametrarna för värd programmet (IP-adress, nätverks adress och nätverks mask) och tar bort statusen för DHCP-klienten på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="28766-366">Den används i kombination med *nx_dhcp_stop* och *nx_dhcp_start* att starta om DHCP-tillstånds datorn:</span><span class="sxs-lookup"><span data-stu-id="28766-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="28766-367">nx_dhcp_stop (&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="28766-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="28766-368">nx_dhcp_reinitialize (&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="28766-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="28766-369">nx_dhcp_start (&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="28766-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="28766-370">Använd tjänsten *nx_dhcp_interface_reinitialize* om du vill initiera DHCP-klienten på ett speciellt gränssnitt när flera gränssnitt är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-371">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-371">Input Parameters</span></span>

- <span data-ttu-id="28766-372">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-373">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-373">Return Values</span></span>

- <span data-ttu-id="28766-374">**NX_SUCCESS** (0X00) DHCP har initierats om</span><span class="sxs-lookup"><span data-stu-id="28766-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="28766-375">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-376">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-376">Allowed From</span></span>

<span data-ttu-id="28766-377">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-378">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="28766-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="28766-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="28766-380">Rensa nätverks parametrarna för DHCP-klienten på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="28766-381">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-382">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-382">Description</span></span>

<span data-ttu-id="28766-383">Den här tjänsten rensar nätverks parametrarna (IP-adress, nätverks adress och nätverks mask) på det angivna gränssnittet om gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="28766-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="28766-384">Se *nx_dhcp_reinitialize* för mer information.</span><span class="sxs-lookup"><span data-stu-id="28766-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-385">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-385">Input Parameters</span></span>

- <span data-ttu-id="28766-386">**dhcp_ptr** Pekare till tidigare skapad DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="28766-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="28766-387">**interface_index** Index för gränssnitt att initiera om.</span><span class="sxs-lookup"><span data-stu-id="28766-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-388">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-388">Return Values</span></span>

- <span data-ttu-id="28766-389">Gränssnittet för **NX_SUCCESS** (0x00) har initierats om</span><span class="sxs-lookup"><span data-stu-id="28766-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="28766-390">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-391">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-392">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="28766-393">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-394">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-394">Allowed From</span></span>

<span data-ttu-id="28766-395">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-396">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="28766-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="28766-397">nx_dhcp_release</span></span>

<span data-ttu-id="28766-398">Frisläpp IP-adress för lån</span><span class="sxs-lookup"><span data-stu-id="28766-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-399">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-400">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-400">Description</span></span>

<span data-ttu-id="28766-401">Den här tjänsten frigör IP-adressen som hämtades från en DHCP-server genom att skicka RELEASE-meddelandet till den servern.</span><span class="sxs-lookup"><span data-stu-id="28766-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="28766-402">Sedan initierar den om DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="28766-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="28766-403">Den här tjänsten används för alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="28766-404">Programmet kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="28766-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="28766-405">Om du vill släppa en adress tillbaka till DHCP-servern i ett gränssnitt använder du tjänsten *nx_dhcp_interface_release*</span><span class="sxs-lookup"><span data-stu-id="28766-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-406">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-406">Input Parameters</span></span>

- <span data-ttu-id="28766-407">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-408">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-408">Return Values</span></span>

- <span data-ttu-id="28766-409">**NX_SUCCESS** (0X00) DHCP-version.</span><span class="sxs-lookup"><span data-stu-id="28766-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="28766-410">**NX_DHCP_NOT_BOUND** (0X94) IP-adressen har inte lånats så den kan inte släppas.</span><span class="sxs-lookup"><span data-stu-id="28766-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="28766-411">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-412">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-413">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-413">Allowed From</span></span>

<span data-ttu-id="28766-414">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-415">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="28766-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="28766-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="28766-417">Frigör IP-adress på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-418">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-419">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-419">Description</span></span>

<span data-ttu-id="28766-420">Den här tjänsten frigör IP-adressen som hämtades från en DHCP-server på det angivna gränssnittet och initierar om DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="28766-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="28766-421">Du kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="28766-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-422">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-422">Input Parameters</span></span>

- <span data-ttu-id="28766-423">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-424">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-424">Return Values</span></span>

- <span data-ttu-id="28766-425">**NX_SUCCESS** (0X00) DHCP-version.</span><span class="sxs-lookup"><span data-stu-id="28766-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="28766-426">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-427">**NX_DHCP_NOT_BOUND** (0X94) IP-adressen har inte lånats så den kan inte släppas.</span><span class="sxs-lookup"><span data-stu-id="28766-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="28766-428">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-429">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="28766-430">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-431">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-431">Allowed From</span></span>

<span data-ttu-id="28766-432">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-433">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="28766-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="28766-434">nx_dhcp_decline</span></span>

<span data-ttu-id="28766-435">Neka IP-adress från DHCP-server</span><span class="sxs-lookup"><span data-stu-id="28766-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-436">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-437">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-437">Description</span></span>

<span data-ttu-id="28766-438">Den här tjänsten avböjer en IP-adress som är lånad från DHCP-servern på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="28766-439">Om NX_DHCP_CLIENT_ SEND_ ARP_PROBE har definierats skickar DHCP-klienten ett neka-meddelande om den identifierar att IP-adressen redan används.</span><span class="sxs-lookup"><span data-stu-id="28766-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="28766-440">Se **ARP-avsökningar** i kapitel ett för mer information om ARP PROBE-konfiguration i netx DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="28766-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="28766-441">Programmet kan använda den här tjänsten för att neka sin IP-adress om den identifierar adressen används på annat sätt.</span><span class="sxs-lookup"><span data-stu-id="28766-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="28766-442">Den här tjänsten initierar om DHCP-klienten så att den kan startas om genom att anropa *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="28766-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-443">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-443">Input Parameters</span></span>

- <span data-ttu-id="28766-444">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-445">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-445">Return Values</span></span>

- <span data-ttu-id="28766-446">**NX_SUCCESS** (0X00) nekad har skickats</span><span class="sxs-lookup"><span data-stu-id="28766-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="28766-447">**NX_DHCP_NOT_STARTED** (0X96) DHCP-instansen startades inte</span><span class="sxs-lookup"><span data-stu-id="28766-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="28766-448">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-449">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="28766-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-450">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-450">Allowed From</span></span>

<span data-ttu-id="28766-451">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-452">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="28766-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="28766-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="28766-454">Neka IP-adress från DHCP-server på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-455">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-456">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-456">Description</span></span>

<span data-ttu-id="28766-457">Den här tjänsten skickar meddelandet neka till servern för att neka en IP-adress som tilldelats av DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="28766-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="28766-458">Den initierar också om DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="28766-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="28766-459">Se *nx_dhcp_decline* för mer information.</span><span class="sxs-lookup"><span data-stu-id="28766-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-460">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-460">Input Parameters</span></span>

- <span data-ttu-id="28766-461">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-462">**Interface_index** Index för gränssnittet för att neka IP-adress</span><span class="sxs-lookup"><span data-stu-id="28766-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-463">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-463">Return Values</span></span>

- <span data-ttu-id="28766-464">**NX_SUCCESS** (0X00) DHCP-neka meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="28766-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="28766-465">**NX_DHCP_NOT_BOUND** (0X94) DHCP-klienten är inte kopplad</span><span class="sxs-lookup"><span data-stu-id="28766-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="28766-466">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-467">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-468">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="28766-469">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-470">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-470">Allowed From</span></span>

<span data-ttu-id="28766-471">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-472">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="28766-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="28766-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="28766-474">Skicka DHCP-meddelande till Server</span><span class="sxs-lookup"><span data-stu-id="28766-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-475">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="28766-476">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-476">Description</span></span>

<span data-ttu-id="28766-477">Den här tjänsten skickar det angivna DHCP-meddelandet till DHCP-servern i det första gränssnitt som är aktiverat för DHCP som finns i DHCP-postposten.</span><span class="sxs-lookup"><span data-stu-id="28766-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="28766-478">Om du vill skicka en version eller avvisa ett meddelande måste programmet använda tjänsterna *nx_dhcp [_interface] _release*() eller *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="28766-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="28766-479">DHCP-klienten måste startas för att använda den här tjänsten, förutom för att skicka INFORM_REQUEST meddelande typen.</span><span class="sxs-lookup"><span data-stu-id="28766-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="28766-480">Den här tjänsten är inte avsedd för värd programmet till enhetens klient tillstånds dator.</span><span class="sxs-lookup"><span data-stu-id="28766-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-481">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-481">Input Parameters</span></span>

- <span data-ttu-id="28766-482">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="28766-483">**dhcp_message_type** Meddelandebegäran (definieras i *nx_dhcp. h*)</span><span class="sxs-lookup"><span data-stu-id="28766-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-484">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-484">Return Values</span></span>

- <span data-ttu-id="28766-485">**NX_SUCCESS** (0X00) DHCP-meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="28766-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="28766-486">**NX_DHCP_NOT_STARTED** (0X96) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="28766-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="28766-487">**NX_DHCP_INVALID_MESSAGE** (0X9B) ogiltig meddelande typ som ska skickas</span><span class="sxs-lookup"><span data-stu-id="28766-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="28766-488">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="28766-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-489">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-489">Allowed From</span></span>

<span data-ttu-id="28766-490">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-491">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="28766-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="28766-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="28766-493">Skicka DHCP-meddelande till server på ett speciellt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-494">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="28766-495">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-495">Description</span></span>

<span data-ttu-id="28766-496">Den här tjänsten skickar ett meddelande till DHCP-servern på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="28766-497">Om du vill skicka en version eller avvisa ett meddelande måste programmet använda tjänsterna *nx_dhcp [_interface] _release*() eller *nx_dhcp_interface_decline ()* .</span><span class="sxs-lookup"><span data-stu-id="28766-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="28766-498">DHCP-klienten måste ha startats för att använda den här tjänsten, förutom för meddelande typen DHCP-meddelande begär Ande.</span><span class="sxs-lookup"><span data-stu-id="28766-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="28766-499">Den här tjänsten är inte avsedd för värd programmet till enhetens klient tillstånds dator.</span><span class="sxs-lookup"><span data-stu-id="28766-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-500">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-500">Input Parameters</span></span>

- <span data-ttu-id="28766-501">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="28766-502">**Interface_index** Index för gränssnitt att skicka meddelande på</span><span class="sxs-lookup"><span data-stu-id="28766-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="28766-503">**dhcp_message_type** Meddelandebegäran (definieras i *nx_dhcp. h*)</span><span class="sxs-lookup"><span data-stu-id="28766-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-504">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-504">Return Values</span></span>

- <span data-ttu-id="28766-505">**NX_SUCCESS** (0X00) DHCP-meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="28766-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="28766-506">**NX_DHCP_NOT_STARTED** (0X96) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="28766-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="28766-507">**NX_DHCP_INVALID_MESSAGE** (0X9B) ogiltig meddelande typ som ska skickas</span><span class="sxs-lookup"><span data-stu-id="28766-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="28766-508">Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="28766-509">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-510">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="28766-511">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-512">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-512">Allowed From</span></span>

<span data-ttu-id="28766-513">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-514">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="28766-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="28766-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="28766-516">Hämta DHCP-klientens DHCP-servers IP-adress</span><span class="sxs-lookup"><span data-stu-id="28766-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-517">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="28766-518">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-518">Description</span></span>

<span data-ttu-id="28766-519">Den här tjänsten hämtar DHCP-klientens DHCP-servers IP-adress i det första gränssnittet som är aktiverat för DHCP som finns i DHCP-postposten.</span><span class="sxs-lookup"><span data-stu-id="28766-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="28766-520">Anroparen kan bara använda den här tjänsten när DHCP-klienten har bundits till en IP-adress som tilldelats av DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="28766-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="28766-521">Värd programmet kan använda tjänsten *nx_ip_status_check* för att kontrol lera att IP-adressen har angetts, eller så kan den använda *nx_dhcp_state_change_notify* och fråga DHCP-klientens tillstånd NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="28766-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="28766-522">Mer information om hur du anger motringnings funktionen för tillstånds ändringar finns i *nx_dhcp_state_change_notify* .</span><span class="sxs-lookup"><span data-stu-id="28766-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="28766-523">Om du vill hitta DHCP-servern på ett speciellt gränssnitt när flera gränssnitt är aktiverade för DHCP-klienten, använder du tjänsten *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="28766-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-524">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-524">Input Parameters</span></span>

- <span data-ttu-id="28766-525">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="28766-526">**server_address** Pekare till serverns IP-adress</span><span class="sxs-lookup"><span data-stu-id="28766-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-527">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-527">Return Values</span></span>

- <span data-ttu-id="28766-528">**NX_SUCCESS** (0X00) DHCP-serveradress returnerades</span><span class="sxs-lookup"><span data-stu-id="28766-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="28766-529">NX_PTR_ERROR (0x16) ogiltig inmatare</span><span class="sxs-lookup"><span data-stu-id="28766-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="28766-530">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-531">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-531">Allowed From</span></span>

<span data-ttu-id="28766-532">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-533">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="28766-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="28766-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="28766-535">Hämta DHCP-klientens DHCP-servers IP-adress på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-536">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="28766-537">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-537">Description</span></span>

<span data-ttu-id="28766-538">Den här tjänsten hämtar DHCP-klientens DHCP-servers IP-adress på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="28766-539">DHCP-klienten måste vara i begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="28766-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="28766-540">När du har startat DHCP-klienten på det här gränssnittet kan värd programmet antingen använda *nx_ip_status_check* tjänsten för att kontrol lera att IP-adressen har angetts, eller så kan den använda DHCP-klientens tillstånd för att ändra motringning och fråga DHCP-klientens tillstånd att NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="28766-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="28766-541">Mer information om hur du anger motringnings funktionen för tillstånds ändringar finns i *nx_dhcp_state_change_notify* .</span><span class="sxs-lookup"><span data-stu-id="28766-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-542">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-542">Input Parameters</span></span>

- <span data-ttu-id="28766-543">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="28766-544">**Interface_index** Index för gränssnitt för att hämta IP-adress</span><span class="sxs-lookup"><span data-stu-id="28766-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="28766-545">**server_address** Pekare till serverns IP-adress</span><span class="sxs-lookup"><span data-stu-id="28766-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-546">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-546">Return Values</span></span>

- <span data-ttu-id="28766-547">**NX_SUCCESS** (0X00) DHCP-serveradress returnerades</span><span class="sxs-lookup"><span data-stu-id="28766-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="28766-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="28766-549">**NX_DHCP_NOT_BOUND** (0X94) DHCP-klienten är inte kopplad</span><span class="sxs-lookup"><span data-stu-id="28766-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="28766-550">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="28766-551">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="28766-552">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-553">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-553">Allowed From</span></span>

<span data-ttu-id="28766-554">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-555">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="28766-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="28766-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="28766-557">Ange nätverks gränssnitt för DHCP-instans</span><span class="sxs-lookup"><span data-stu-id="28766-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-558">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="28766-559">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-559">Description</span></span>

<span data-ttu-id="28766-560">Den här tjänsten anger nätverks gränssnittet för DHCP-instansen att ansluta till DHCP-servern vid körning av DHCP-klienten som kon figurer ATS för ett enda nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="28766-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="28766-561">Som standard körs DHCP-klienten på det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="28766-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="28766-562">Om du vill köra DHCP på en sekundär tjänst använder du den här tjänsten för att ange det sekundära gränssnittet som DHCP-klient gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="28766-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="28766-563">Programmet måste tidigare registrera det angivna gränssnittet för IP-instansen med hjälp av tjänsten *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="28766-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="28766-564">Observera att den här tjänsten är avsedd för program som endast avser att köra DHCP-klienten på ett gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="28766-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="28766-565">Om du vill köra DHCP på flera gränssnitt kan du se *nx_dhcp_interface_enable* för mer information.</span><span class="sxs-lookup"><span data-stu-id="28766-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-566">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-566">Input Parameters</span></span>

- <span data-ttu-id="28766-567">**dhcp_ptr** Pekare till DHCP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="28766-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="28766-568">**index** Index för enhetens nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-569">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-569">Return Values</span></span>

- <span data-ttu-id="28766-570">Gränssnittet för **NX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="28766-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="28766-571">**NX_INVALID_INTERFACE** (0X4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="28766-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** -gränssnitt (0xA3) aktiverat för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="28766-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) ingen post tillgänglig för en annan</span><span class="sxs-lookup"><span data-stu-id="28766-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="28766-574">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare</span><span class="sxs-lookup"><span data-stu-id="28766-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-575">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-575">Allowed From</span></span>

<span data-ttu-id="28766-576">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-577">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="28766-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="28766-578">nx_dhcp_start</span></span>

<span data-ttu-id="28766-579">Starta DHCP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="28766-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-580">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-581">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-581">Description</span></span>

<span data-ttu-id="28766-582">Den här tjänsten startar DHCP-bearbetning på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="28766-583">Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="28766-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="28766-584">Om du vill kontrol lera att IP-instansen är kopplad till en IP-adress i DHCP-klientens gränssnitt använder du *nx_ip_status_check* för att se bekräfta att IP-adressen är giltig.</span><span class="sxs-lookup"><span data-stu-id="28766-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="28766-585">Om det finns andra gränssnitt som redan kör DHCP, kommer den här tjänsten inte att påverka dem.</span><span class="sxs-lookup"><span data-stu-id="28766-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="28766-586">Använd tjänsten *nx_dhcp_interface_start* för att starta DHCP på ett speciellt gränssnitt när flera gränssnitt är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="28766-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-587">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-587">Input Parameters</span></span>

- <span data-ttu-id="28766-588">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-589">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-589">Return Values</span></span>

- <span data-ttu-id="28766-590">**NX_SUCCESS** (0X00) DHCP-start har slutförts.</span><span class="sxs-lookup"><span data-stu-id="28766-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="28766-591">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="28766-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="28766-592">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-593">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="28766-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-594">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-594">Allowed From</span></span>

<span data-ttu-id="28766-595">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-596">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="28766-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="28766-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="28766-598">Starta DHCP-bearbetning på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-599">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-600">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-600">Description</span></span>

<span data-ttu-id="28766-601">Den här tjänsten startar DHCP-bearbetning på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="28766-602">Se *nx_dhcp_interface_enable*() om du vill ha mer information om hur du aktiverar ett gränssnitt för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="28766-603">Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="28766-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="28766-604">Om det inte finns några andra gränssnitt som kör DHCP-klienten, kommer tjänsten att starta/återuppta DHCP-klientens tråd och (åter) Aktivera DHCP-klientens timer.</span><span class="sxs-lookup"><span data-stu-id="28766-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="28766-605">Programmet bör använda *nx_ip_status_check* för att kontrol lera om en IP-adress hämtas.</span><span class="sxs-lookup"><span data-stu-id="28766-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-606">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-606">Input Parameters</span></span>

- <span data-ttu-id="28766-607">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-608">**Interface_index** Index för att starta DHCP-klienten</span><span class="sxs-lookup"><span data-stu-id="28766-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-609">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-609">Return Values</span></span>

- <span data-ttu-id="28766-610">**NX_SUCCESS** (0X00) DHCP-start har slutförts.</span><span class="sxs-lookup"><span data-stu-id="28766-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="28766-611">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP-instansen har redan startats.</span><span class="sxs-lookup"><span data-stu-id="28766-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="28766-612">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-613">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="28766-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="28766-614">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-615">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-615">Allowed From</span></span>

<span data-ttu-id="28766-616">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-617">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="28766-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="28766-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="28766-619">Ange funktion för att ändra motringning för DHCP-tillstånd</span><span class="sxs-lookup"><span data-stu-id="28766-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-620">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="28766-621">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-621">Description</span></span>

<span data-ttu-id="28766-622">Den här tjänsten registrerar den angivna återanrops funktionen dhcp_state_change_notify för att meddela ett program om DHCP-tillstånds ändringar.</span><span class="sxs-lookup"><span data-stu-id="28766-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="28766-623">Funktionen motringning tillhandahåller det tillstånd som DHCP-klienten har övergått till.</span><span class="sxs-lookup"><span data-stu-id="28766-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="28766-624">Följande är värden som är associerade med de olika DHCP-tillstånden:</span><span class="sxs-lookup"><span data-stu-id="28766-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="28766-625">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="28766-625">State</span></span>                             | <span data-ttu-id="28766-626">Värde</span><span class="sxs-lookup"><span data-stu-id="28766-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="28766-627">start av NX \_ DHCP- \_ tillstånd \_</span><span class="sxs-lookup"><span data-stu-id="28766-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="28766-628">1</span><span class="sxs-lookup"><span data-stu-id="28766-628">1</span></span>     |
| <span data-ttu-id="28766-629">initiering av NX \_ DHCP- \_ tillstånd \_</span><span class="sxs-lookup"><span data-stu-id="28766-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="28766-630">2</span><span class="sxs-lookup"><span data-stu-id="28766-630">2</span></span>     |
| <span data-ttu-id="28766-631">Val av NX \_ DHCP- \_ tillstånd \_</span><span class="sxs-lookup"><span data-stu-id="28766-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="28766-632">3</span><span class="sxs-lookup"><span data-stu-id="28766-632">3</span></span>     |
| <span data-ttu-id="28766-633">\_begär ande av NX DHCP- \_ tillstånd \_</span><span class="sxs-lookup"><span data-stu-id="28766-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="28766-634">4</span><span class="sxs-lookup"><span data-stu-id="28766-634">4</span></span>     |
| <span data-ttu-id="28766-635">\_giltiga NX DHCP- \_ tillstånd \_</span><span class="sxs-lookup"><span data-stu-id="28766-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="28766-636">5</span><span class="sxs-lookup"><span data-stu-id="28766-636">5</span></span>     |
| <span data-ttu-id="28766-637">NX \_ DHCP- \_ tillstånd \_ förnyar</span><span class="sxs-lookup"><span data-stu-id="28766-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="28766-638">6</span><span class="sxs-lookup"><span data-stu-id="28766-638">6</span></span>     |
| <span data-ttu-id="28766-639">OMBINDNING av NX \_ DHCP- \_ tillstånd \_</span><span class="sxs-lookup"><span data-stu-id="28766-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="28766-640">7</span><span class="sxs-lookup"><span data-stu-id="28766-640">7</span></span>     |
| <span data-ttu-id="28766-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="28766-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="28766-642">8</span><span class="sxs-lookup"><span data-stu-id="28766-642">8</span></span>     |
| <span data-ttu-id="28766-643">NX \_ DHCP- \_ tillstånd \_ adress för \_ avsökning</span><span class="sxs-lookup"><span data-stu-id="28766-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="28766-644">9</span><span class="sxs-lookup"><span data-stu-id="28766-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="28766-645">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-645">Input Parameters</span></span>

- <span data-ttu-id="28766-646">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-647">**dhcp_state_change_notify** Funktions pekare för motringning av tillstånds ändring</span><span class="sxs-lookup"><span data-stu-id="28766-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-648">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-648">Return Values</span></span>

- <span data-ttu-id="28766-649">**NX_SUCCESS** (0x00) motringning har angetts.</span><span class="sxs-lookup"><span data-stu-id="28766-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="28766-650">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-651">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="28766-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-652">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-652">Allowed From</span></span>

<span data-ttu-id="28766-653">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="28766-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="28766-654">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="28766-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="28766-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="28766-656">Ange funktionen motringning av DHCP-tillstånd i det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-657">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="28766-658">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-658">Description</span></span>

<span data-ttu-id="28766-659">Den här tjänsten registrerar den angivna callback-funktionen för att meddela ett program om DHCP-tillstånds ändringar.</span><span class="sxs-lookup"><span data-stu-id="28766-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="28766-660">Funciton för motringning är gränssnitts index och det tillstånd som DHCP-klienten har övergått till på det gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="28766-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="28766-661">Mer information om tillstånds ändrings funktioner finns i *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="28766-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-662">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-662">Input Parameters</span></span>

- <span data-ttu-id="28766-663">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-664">**dhcp_interface_state_change_notify** Funktions pekare för program återanrop</span><span class="sxs-lookup"><span data-stu-id="28766-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-665">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-665">Return Values</span></span>

- <span data-ttu-id="28766-666">**NX_SUCCESS** (0x00) motringning har angetts.</span><span class="sxs-lookup"><span data-stu-id="28766-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="28766-667">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-668">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-668">Allowed From</span></span>

<span data-ttu-id="28766-669">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="28766-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="28766-670">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="28766-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="28766-671">nx_dhcp_stop</span></span>

<span data-ttu-id="28766-672">Stoppar DHCP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="28766-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-673">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-674">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-674">Description</span></span>

<span data-ttu-id="28766-675">Den här tjänsten stoppar DHCP-bearbetning på alla gränssnitt som har börjat DHCP-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="28766-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="28766-676">Om det inte finns några gränssnitt som bearbetar DHCP kommer den här tjänsten att pausa DHCP-klientens tråd och inaktivera DHCP-klientens timer.</span><span class="sxs-lookup"><span data-stu-id="28766-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="28766-677">Använd tjänsten *nx_dhcp_interface_stop* för att stoppa DHCP på ett speciellt gränssnitt om flera gränssnitt är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-678">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-678">Input Parameters</span></span>

- <span data-ttu-id="28766-679">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-680">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-680">Return Values</span></span>

- <span data-ttu-id="28766-681">**NX_SUCCESS** (0X00) DHCP-stopp</span><span class="sxs-lookup"><span data-stu-id="28766-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="28766-682">**NX_DHCP_NOT_STARTED** (0X96) DHCP-instansen startades inte.</span><span class="sxs-lookup"><span data-stu-id="28766-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="28766-683">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-684">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="28766-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-685">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-685">Allowed From</span></span>

<span data-ttu-id="28766-686">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-687">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="28766-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="28766-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="28766-689">Stoppa DHCP-bearbetning på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-690">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="28766-691">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-691">Description</span></span>

<span data-ttu-id="28766-692">Den här tjänsten stoppar DHCP-bearbetning på det angivna gränssnittet om DHCP redan har startats.</span><span class="sxs-lookup"><span data-stu-id="28766-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="28766-693">Om det inte finns några andra gränssnitt som kör DHCP så pausas DHCP-tråden och timern.</span><span class="sxs-lookup"><span data-stu-id="28766-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-694">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-694">Input Parameters</span></span>

- <span data-ttu-id="28766-695">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-696">**Interface_index** Gränssnitt där DHCP-bearbetningen ska stoppas</span><span class="sxs-lookup"><span data-stu-id="28766-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-697">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-697">Return Values</span></span>

- <span data-ttu-id="28766-698">**NX_SUCCESS** (0X00) DHCP-stopp</span><span class="sxs-lookup"><span data-stu-id="28766-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="28766-699">**NX_DHCP_NOT_STARTED** (0X96) DHCP har inte startats.</span><span class="sxs-lookup"><span data-stu-id="28766-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="28766-700">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-701">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="28766-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="28766-702">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-703">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-703">Allowed From</span></span>

<span data-ttu-id="28766-704">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-705">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="28766-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="28766-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="28766-707">Hämta ett DHCP-alternativ från senaste Server svar</span><span class="sxs-lookup"><span data-stu-id="28766-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-708">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="28766-709">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-709">Description</span></span>

<span data-ttu-id="28766-710">Den här tjänsten hämtar det angivna DHCP-alternativet från bufferten för DHCP-alternativ i det första gränssnitt som är aktiverat för DHCP som finns på DHCP-klienttjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="28766-711">Om det lyckas kopieras alternativ data till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="28766-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-712">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-712">Input Parameters</span></span>

- <span data-ttu-id="28766-713">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="28766-714">**request_option** DHCP-alternativet, enligt vad som anges i RFC: erna.</span><span class="sxs-lookup"><span data-stu-id="28766-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="28766-715">Se alternativet NX_DHCP_OPTION i *nx_dhcp. h*.</span><span class="sxs-lookup"><span data-stu-id="28766-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="28766-716">**destination_ptr** Pekar till målet för svars strängen.</span><span class="sxs-lookup"><span data-stu-id="28766-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="28766-717">**destination_size** Pekar till målets storlek och vid retur, där antalet byte som returneras visas.</span><span class="sxs-lookup"><span data-stu-id="28766-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-718">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-718">Return Values</span></span>

- <span data-ttu-id="28766-719">Hämtning av **NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="28766-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="28766-720">**NX_DHCP_NOT_BOUND** (0X94) DHCP-klienten är inte kopplad.</span><span class="sxs-lookup"><span data-stu-id="28766-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="28766-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="28766-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="28766-722">**NX_DHCP_DEST_TO_SMALL** -destinationen (0x95) är för liten för att rymma svar.</span><span class="sxs-lookup"><span data-stu-id="28766-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="28766-723">Det gick inte att hitta **NX_DHCP_PARSE_ERROR** (0X97) DHCP-alternativet i Server svaret.</span><span class="sxs-lookup"><span data-stu-id="28766-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="28766-724">NX_PTR_ERROR (0x16) ogiltig inmatad pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="28766-725">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="28766-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-726">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-726">Allowed From</span></span>

<span data-ttu-id="28766-727">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-728">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="28766-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="28766-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="28766-730">Hämta ett DHCP-alternativ från senaste Server svar på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="28766-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-731">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="28766-732">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-732">Description</span></span>

<span data-ttu-id="28766-733">Den här tjänsten hämtar det angivna DHCP-alternativet från bufferten för DHCP-alternativ på det angivna gränssnittet, om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="28766-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="28766-734">Om det lyckas kopieras alternativ data till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="28766-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-735">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-735">Input Parameters</span></span>

- <span data-ttu-id="28766-736">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-737">**Interface_index** Index som det angivna alternativet ska hämtas till</span><span class="sxs-lookup"><span data-stu-id="28766-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="28766-738">**request_option** DHCP-alternativet, enligt vad som anges i RFC: erna.</span><span class="sxs-lookup"><span data-stu-id="28766-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="28766-739">Se alternativet NX_DHCP_OPTION i *nx_dhcp. h*.</span><span class="sxs-lookup"><span data-stu-id="28766-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="28766-740">**destination_ptr** Pekar till målet för svars strängen.</span><span class="sxs-lookup"><span data-stu-id="28766-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="28766-741">**destination_size** Pekar till målets storlek och vid retur, där antalet byte som returneras visas.</span><span class="sxs-lookup"><span data-stu-id="28766-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-742">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-742">Return Values</span></span>

- <span data-ttu-id="28766-743">Hämtning av **NX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="28766-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="28766-744">**NX_DHCP_NOT_BOUND** (0X94) IP-adress inte tilldelad</span><span class="sxs-lookup"><span data-stu-id="28766-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="28766-745">**NX_DHCP_DEST_TO_SMALL** -bufferten (0x95) är för liten</span><span class="sxs-lookup"><span data-stu-id="28766-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="28766-746">Det gick inte att hitta **NX_DHCP_PARSE_ERROR** (0X97) DHCP-alternativet i Server svaret.</span><span class="sxs-lookup"><span data-stu-id="28766-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="28766-747">NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="28766-748">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="28766-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="28766-749">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="28766-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-750">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-750">Allowed From</span></span>

<span data-ttu-id="28766-751">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-752">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="28766-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="28766-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="28766-754">Konvertera fyra byte till ULONG</span><span class="sxs-lookup"><span data-stu-id="28766-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-755">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="28766-756">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-756">Description</span></span>

<span data-ttu-id="28766-757">Den här tjänsten konverterar de fyra tecknen till "option_string_ptr" till ett osignerat långt värde.</span><span class="sxs-lookup"><span data-stu-id="28766-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="28766-758">Det är särskilt användbart när det finns IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="28766-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-759">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-759">Input Parameters</span></span>

- <span data-ttu-id="28766-760">**option_string_ptr** Pekare till den tidigare hämtade alternativ strängen.</span><span class="sxs-lookup"><span data-stu-id="28766-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-761">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-761">Return Values</span></span>

- <span data-ttu-id="28766-762">**Värde** Värdet för de första fyra bytena.</span><span class="sxs-lookup"><span data-stu-id="28766-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-763">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-763">Allowed From</span></span>

<span data-ttu-id="28766-764">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-765">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="28766-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="28766-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="28766-767">Ange callback-funktionen för att lägga till användar alternativ som har angetts</span><span class="sxs-lookup"><span data-stu-id="28766-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="28766-768">Prototyp</span><span class="sxs-lookup"><span data-stu-id="28766-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="28766-769">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28766-769">Description</span></span>

<span data-ttu-id="28766-770">Den här tjänsten registrerar den angivna callback-funktionen för att lägga till användar alternativ.</span><span class="sxs-lookup"><span data-stu-id="28766-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="28766-771">Om funktionen motringning har angetts kan programmen lägga till användar alternativ i paketet genom iface_index och message_type.</span><span class="sxs-lookup"><span data-stu-id="28766-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="28766-772">I användarens rutin.</span><span class="sxs-lookup"><span data-stu-id="28766-772">In user’s routine.</span></span> <span data-ttu-id="28766-773">Program måste följa alternativen för DHCP-alternativ när du lägger till användar alternativ.</span><span class="sxs-lookup"><span data-stu-id="28766-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="28766-774">Den totala storleken för användar alternativ måste vara mindre än eller lika med user_option_length och uppdatera user_option_length som en verklig längd.</span><span class="sxs-lookup"><span data-stu-id="28766-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="28766-775">Returnera NX_TRUE om alternativet har lagts till, annars returnerar NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="28766-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="28766-776">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="28766-776">Input Parameters</span></span>

- <span data-ttu-id="28766-777">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="28766-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="28766-778">**dhcp_user_option_add** Pekare till funktionen Lägg till användar alternativ.</span><span class="sxs-lookup"><span data-stu-id="28766-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="28766-779">Retur värden</span><span class="sxs-lookup"><span data-stu-id="28766-779">Return Values</span></span>

- <span data-ttu-id="28766-780">**NX_SUCCESS** (0x00) motringning har angetts.</span><span class="sxs-lookup"><span data-stu-id="28766-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="28766-781">NX_PTR_ERROR (0x16) ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="28766-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="28766-782">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="28766-782">Allowed From</span></span>

<span data-ttu-id="28766-783">Konversation</span><span class="sxs-lookup"><span data-stu-id="28766-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="28766-784">Exempel</span><span class="sxs-lookup"><span data-stu-id="28766-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
