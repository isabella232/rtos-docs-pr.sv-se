---
title: Bilaga A – Beskrivning av funktionen återställnings tillstånd för Azure återställnings tider NetX Duo DHCPv6-klienten
description: Konfigurations alternativet för Azure återställnings tider NetX Duo DHDPv6-klienten NX_DHCPV6_CLIENT_RESTORE_STATE, gör det möjligt för ett system att återställa en tidigare skapad DHCP-klient i ett begränsat tillstånd mellan omstarter av systemet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826100"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="f32a5-103">Bilaga A – Beskrivning av funktionen återställnings tillstånd för Azure återställnings tider NetX Duo DHCPv6-klienten</span><span class="sxs-lookup"><span data-stu-id="f32a5-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="f32a5-104">Konfigurations alternativet för Azure återställnings tider NetX Duo DHDPv6-klienten NX_DHCPV6_CLIENT_RESTORE_STATE, gör det möjligt för ett system att återställa en tidigare skapad DHCP-klient i ett begränsat tillstånd mellan omstarter av systemet.</span><span class="sxs-lookup"><span data-stu-id="f32a5-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="f32a5-105">Det här alternativet gör det också möjligt för ett program att pausa DHCPv6-klient tråden och återuppta den, uppdaterat med den tid som förflutit mellan att pausa och återuppta tråden utan att behöva stänga av den.</span><span class="sxs-lookup"><span data-stu-id="f32a5-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="f32a5-106">Återställa DHCPv6-klienten mellan omstarter</span><span class="sxs-lookup"><span data-stu-id="f32a5-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="f32a5-107">För att återställa en DHCPv6-klient mellan omstarter skapar DHCPv6-programmet en instans av DHCPv6-klienten och erhåller sedan ett IP-adresslån med det normala DHCPv6-protokollet och anropar *nx_dhcpv6_start*.</span><span class="sxs-lookup"><span data-stu-id="f32a5-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="f32a5-108">DHCPv6-programmet väntar sedan på att protokollet ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="f32a5-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="f32a5-109">Om alla går bra, uppnår enheten BINDNINGs tillstånd med en tilldelad giltig IP-adress från DHCPv6-servern.</span><span class="sxs-lookup"><span data-stu-id="f32a5-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="f32a5-110">Innan den stängs av sparar DHCPv6-klient programmet den aktuella DHCPv6-klient instansen till en DHCPv6-klient post som sedan lagras i beständigt minne.</span><span class="sxs-lookup"><span data-stu-id="f32a5-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="f32a5-111">En oberoende "tidsbehållare" i systemet håller reda på den tid som förflutit under det här tillstånd som är avstängd.</span><span class="sxs-lookup"><span data-stu-id="f32a5-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="f32a5-112">Vid inaktive rad skapar programmet en ny DHCPv6-klient instans och uppdaterar den sedan med den tidigare skapade DHCPv6-klient posten.</span><span class="sxs-lookup"><span data-stu-id="f32a5-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="f32a5-113">Tiden som förflutit hämtas från "tids hållaren" och tillämpas sedan på den tid som återstår av DHCP-Clientv6 lån.</span><span class="sxs-lookup"><span data-stu-id="f32a5-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="f32a5-114">I det här läget kan programmet återuppta DHCPv6-klienten.</span><span class="sxs-lookup"><span data-stu-id="f32a5-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="f32a5-115">Om den tid som förflutit under avstängning ger DHCPv6-klientens tillstånd i antingen förnyelse eller OMBINDNING, initierar DHCPv6-klienten automatiskt DHCPv6-meddelanden som begär att förnya eller ombinda IP-adresslån.</span><span class="sxs-lookup"><span data-stu-id="f32a5-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="f32a5-116">Om IP-adressen har upphört att gälla rensar DHCPv6-klienten automatiskt IP-adressen på IP-instansen och påbörjar DHCPv6-processen från INIT-tillståndet och begär en ny IP-adress.</span><span class="sxs-lookup"><span data-stu-id="f32a5-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="f32a5-117">På så sätt kan DHCPv6-klienten köras mellan omstarter som om de är avbrutna.</span><span class="sxs-lookup"><span data-stu-id="f32a5-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="f32a5-118">Nedan visas en illustration av den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="f32a5-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="f32a5-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="f32a5-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="f32a5-120">Skapa en post för aktuellt DHCPv6-klient tillstånd</span><span class="sxs-lookup"><span data-stu-id="f32a5-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="f32a5-121">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f32a5-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="f32a5-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f32a5-122">Description</span></span>

<span data-ttu-id="f32a5-123">Den här tjänsten sparar DHCPv6-klienten till posten som pekas av record_ptr.</span><span class="sxs-lookup"><span data-stu-id="f32a5-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="f32a5-124">Detta gör att DHCPv6-klientens program kan återställa sitt DHCPv6-klient tillstånd efter, till exempel en avstängning och omstart.</span><span class="sxs-lookup"><span data-stu-id="f32a5-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f32a5-125">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f32a5-125">Input Parameters</span></span>

- <span data-ttu-id="f32a5-126">**dhcpv6_ptr** Pekare till DHCPv6-klienten</span><span class="sxs-lookup"><span data-stu-id="f32a5-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="f32a5-127">**record_ptr** Pekare till DHCPv6-klient post</span><span class="sxs-lookup"><span data-stu-id="f32a5-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="f32a5-128">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f32a5-128">Return Values</span></span>

- <span data-ttu-id="f32a5-129">**NX_SUCCESS (0x0)** En giltig klient post har skapats</span><span class="sxs-lookup"><span data-stu-id="f32a5-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="f32a5-130">**NX_DHCPV6_NOT_BOUND** -klienten (0xE94) är inte i ett begränsat tillstånd och har därför inte tilldelats någon giltig IP-adress</span><span class="sxs-lookup"><span data-stu-id="f32a5-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="f32a5-131">**NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="f32a5-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f32a5-132">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f32a5-132">Allowed From</span></span>

<span data-ttu-id="f32a5-133">Konversation</span><span class="sxs-lookup"><span data-stu-id="f32a5-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f32a5-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="f32a5-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="f32a5-135">Se även</span><span class="sxs-lookup"><span data-stu-id="f32a5-135">See Also</span></span>

- <span data-ttu-id="f32a5-136">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="f32a5-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="f32a5-137">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="f32a5-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="f32a5-138">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="f32a5-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="f32a5-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="f32a5-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="f32a5-140">Återställa DHCPv6-klient tillstånd från sparad post</span><span class="sxs-lookup"><span data-stu-id="f32a5-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="f32a5-141">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f32a5-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="f32a5-142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f32a5-142">Description</span></span>

<span data-ttu-id="f32a5-143">Den här tjänsten gör det möjligt för ett DHCPv6-program att återskapa sitt DHCPv6-klient tillstånd från en tidigare session genom att uppdatera DHCPv6-klienten med DHCPv6-klient posten som record_ptr, och uppdaterar den tid som återstår på DHCPv6-klient lånet med time_elapsed indata.</span><span class="sxs-lookup"><span data-stu-id="f32a5-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="f32a5-144">Detta gör att DHCPv6-klient programmet återskapar sin DHCPv6-klient, till exempel efter en avstängning.</span><span class="sxs-lookup"><span data-stu-id="f32a5-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="f32a5-145">Detta kräver att DHCPv6-klient programmet har skapat en post för DHCPv6-klienten innan den stängs av och sparar posten till icke-flyktigt minne.</span><span class="sxs-lookup"><span data-stu-id="f32a5-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f32a5-146">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f32a5-146">Input Parameters</span></span>

- <span data-ttu-id="f32a5-147">**dhcpv6_ptr** Pekare till DHCPv6-klienten</span><span class="sxs-lookup"><span data-stu-id="f32a5-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="f32a5-148">**record_ptr** Pekare till DHCPv6-klient post</span><span class="sxs-lookup"><span data-stu-id="f32a5-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="f32a5-149">**time_elapsed** Tid för att ta bort från den återstående låne tiden i posten för indata-klienten</span><span class="sxs-lookup"><span data-stu-id="f32a5-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="f32a5-150">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f32a5-150">Return Values</span></span>

- <span data-ttu-id="f32a5-151">**NX_SUCCESS (0x0)** Klient post återställd</span><span class="sxs-lookup"><span data-stu-id="f32a5-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="f32a5-152">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="f32a5-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f32a5-153">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f32a5-153">Allowed From</span></span>

<span data-ttu-id="f32a5-154">Konversation</span><span class="sxs-lookup"><span data-stu-id="f32a5-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f32a5-155">Exempel</span><span class="sxs-lookup"><span data-stu-id="f32a5-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="f32a5-156">Se även</span><span class="sxs-lookup"><span data-stu-id="f32a5-156">See Also</span></span>

- <span data-ttu-id="f32a5-157">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="f32a5-157">nx_dhcpv6_client_get_record</span></span>