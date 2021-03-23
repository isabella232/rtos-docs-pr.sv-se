---
title: Bilaga A – Beskrivning av funktionen Restore State för Azure återställnings tider NetX Duo DHCP Client Services
description: Det här kapitlet innehåller en beskrivning av funktionen Restore State för Azure återställnings tider NetX Duo DHCP Client Services.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826145"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="35e9a-103">Bilaga A: Beskrivning av funktionen Restore State för Azure återställnings tider NetX Duo DHCP Client Services</span><span class="sxs-lookup"><span data-stu-id="35e9a-103">Appendix A : Description of the Restore state feature for Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="35e9a-104">Klient konfigurations alternativet NetX Duo DHDP NX_DHCP_CLIENT_RESTORE_STATE, gör att ett system kan återställa en tidigare skapad DHCP-resurspost i ett begränsat tillstånd mellan omstarter av systemet.</span><span class="sxs-lookup"><span data-stu-id="35e9a-104">The NetX Duo DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="35e9a-105">När det här alternativet är aktiverat kan programmet pausa och återuppta DHCP-klientens tråd.</span><span class="sxs-lookup"><span data-stu-id="35e9a-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="35e9a-106">Det finns också en tjänst för att uppdatera DHCP-klienten med förfluten tid mellan att pausa och återuppta tråden.</span><span class="sxs-lookup"><span data-stu-id="35e9a-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="35e9a-107">Återställa DHCP-klienten mellan omstarter</span><span class="sxs-lookup"><span data-stu-id="35e9a-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="35e9a-108">Innan du återställer en DHCP-klient efter omstart, måste du ha en tidigare skapad DHCP-klient som måste komma åt bindnings statusen och tilldelas en IP-adress från DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="35e9a-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="35e9a-109">Innan den stängs av måste DHCP-programmet spara den aktuella posten för DHCP-klienten till icke-flyktigt minne.</span><span class="sxs-lookup"><span data-stu-id="35e9a-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="35e9a-110">Det måste också finnas en oberoende "tidsbehållare" i systemet för att hålla reda på hur lång tid som förflutit under det här läget är avstängd.</span><span class="sxs-lookup"><span data-stu-id="35e9a-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="35e9a-111">Vid inaktive rad skapar programmet en ny DHCP-klient instans och uppdaterar den sedan med den tidigare skapade DHCP-klientprogramvaran.</span><span class="sxs-lookup"><span data-stu-id="35e9a-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="35e9a-112">Tiden som förflutit hämtas från "tids hållaren" och tillämpas sedan på den tid som återstår av DHCP-klientens lån.</span><span class="sxs-lookup"><span data-stu-id="35e9a-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="35e9a-113">Observera att detta kan leda till att DHCP-klienten ändrar tillstånd, t. ex. från gräns till FÖRNYAnde.</span><span class="sxs-lookup"><span data-stu-id="35e9a-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="35e9a-114">I det här läget kan programmet återuppta DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="35e9a-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="35e9a-115">Om den tid som förflutit under avstängning ger DHCP-klientens tillstånd antingen förnyelse eller OMBINDNING, initierar DHCP-klienten automatiskt DHCP-meddelanden som begär att förnya eller ombinda IP-adresslån.</span><span class="sxs-lookup"><span data-stu-id="35e9a-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="35e9a-116">Om IP-adressen har upphört att gälla rensar DHCP-klienten automatiskt IP-adressen på IP-instansen och startar DHCP-processen från INIT-tillståndet och begär en ny IP-adress.</span><span class="sxs-lookup"><span data-stu-id="35e9a-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="35e9a-117">På så sätt kan DHCP-klienten arbeta mellan omstarter som om de är avbrutna.</span><span class="sxs-lookup"><span data-stu-id="35e9a-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="35e9a-118">Nedan visas en illustration av den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="35e9a-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="35e9a-119">Detta förutsätter att DHCP-klienten bara körs på det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="35e9a-119">This assumes DHCP Client is running only on the primary interface.</span></span>

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
    } while (status != NX_SUCCESS);

    /* We have a valid IP address. */
    /* At some point decide we power down the system. */
    /* Save the Client state data which we will subsequently need to restore the DHCP    
       Client. */
    status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);               

    /* Copy this memory to non-volatile memory (not shown). */
    /* Delete the IP and DHCP Client instances before powering down. */
    nx_dhcp_delete(&dhcp_0);

    nx_ip_delete(&ip_0);
    /* Ready to power down, having released other resources as necessary. */

}
else
{

    /* The application has determined there is a previously saved record. We will 
        restore it to the current DHCP Client instance.  */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
        update the IP instance with IP address, mask etc. */
    status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

    if (status != NX_SUCCESS)
        return;

    /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
    status = nx_dhcp_resume(&dhcp_0);

    if (status != NX_SUCCESS)
        return;

}
```
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="35e9a-120">Återuppta DHCP-klientens tråd efter avbrott</span><span class="sxs-lookup"><span data-stu-id="35e9a-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="35e9a-121">Om du vill pausa en DHCP-klient tråd utan att stänga av, anropar programmet *nx_dhcp_suspend* på en DHCP-klient som har uppnått bindnings status och som har en giltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="35e9a-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="35e9a-122">När den är redo att återuppta DHCP-klienten anropas den först *nx_dhcp_client_update_time_remaining* för att uppdatera tiden som återstår av DHCP-adresslån (hämtning av den tid som förflutit från en oberoende tids hållare).</span><span class="sxs-lookup"><span data-stu-id="35e9a-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="35e9a-123">Sedan anropas *nx_dhcp_resume* för att återuppta DHCP-klientens tråd.</span><span class="sxs-lookup"><span data-stu-id="35e9a-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="35e9a-124">Om den tid som förflutit sätter DHCP-klientens tillstånd i antingen förnyelse-eller återbinding-tillstånd initierar DHCP-klienten automatiskt DHCP-meddelanden som begär att förnya eller ombinda IP-adresslån.</span><span class="sxs-lookup"><span data-stu-id="35e9a-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="35e9a-125">Om IP-adressen har upphört att gälla rensar DHCP-klienten automatiskt IP-adressen och startar DHCP-processen från INIT-tillståndet och begär en ny IP-adress.</span><span class="sxs-lookup"><span data-stu-id="35e9a-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="35e9a-126">Nedan visas en illustration av hur du använder den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="35e9a-126">Below is an illustration of using this feature.</span></span>

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}

```
<span data-ttu-id="35e9a-127">Nedan visas en lista över tjänster för att återställa en DHCP-klients tillstånd från minnet och för att pausa och återuppta DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="35e9a-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="35e9a-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="35e9a-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="35e9a-129">Skapa en post med det aktuella DHCP-klientens tillstånd</span><span class="sxs-lookup"><span data-stu-id="35e9a-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-130">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-130">Prototype</span></span>

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="35e9a-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-131">Description</span></span>

<span data-ttu-id="35e9a-132">Den här tjänsten sparar DHCP-klienten som körs på det första gränssnittet som är aktiverat för DHCP som finns på DHCP-klientcertifikatet till posten som pekas på av record_ptr.</span><span class="sxs-lookup"><span data-stu-id="35e9a-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="35e9a-133">Detta gör att DHCP-klientprogrammet kan återställa sitt DHCP-klient tillstånd efter, till exempel en avstängning och omstart.</span><span class="sxs-lookup"><span data-stu-id="35e9a-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="35e9a-134">Om du vill spara en DHCP-resurspost på ett gränssnitt om fler än ett gränssnitt har Aktiver ATS för DHCP använder du tjänsten *nx_dhcp_interface_client_get_record* .</span><span class="sxs-lookup"><span data-stu-id="35e9a-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-135">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-135">Input Parameters</span></span>

- <span data-ttu-id="35e9a-136">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-136">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="35e9a-137">**record_ptr**: pekare till posten DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-137">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-138">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-138">Return Values</span></span>

- <span data-ttu-id="35e9a-139">**NX_SUCCESS (0x0)**: klient posten har skapats</span><span class="sxs-lookup"><span data-stu-id="35e9a-139">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="35e9a-140">**NX_DHCP_NOT_BOUND**: (0X94) klienten är inte i ett begränsat tillstånd</span><span class="sxs-lookup"><span data-stu-id="35e9a-140">**NX_DHCP_NOT_BOUND**: (0x94) Client not in Bound states</span></span>
- <span data-ttu-id="35e9a-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="35e9a-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="35e9a-142">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="35e9a-142">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-143">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-143">Allowed From</span></span>

<span data-ttu-id="35e9a-144">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-145">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="35e9a-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="35e9a-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="35e9a-147">Skapa en post för det aktuella DHCP-klientens tillstånd på det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="35e9a-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-148">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-148">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="35e9a-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-149">Description</span></span>

<span data-ttu-id="35e9a-150">Den här tjänsten sparar DHCP-klienten som körs på det angivna gränssnittet till posten som pekas av record_ptr.</span><span class="sxs-lookup"><span data-stu-id="35e9a-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="35e9a-151">Detta gör att DHCP-klientprogrammet kan återställa sitt DHCP-klient tillstånd efter, till exempel en avstängning och omstart.</span><span class="sxs-lookup"><span data-stu-id="35e9a-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-152">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-152">Input Parameters</span></span>

- <span data-ttu-id="35e9a-153">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-153">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="35e9a-154">**interface_index**: indexet som posten ska hämtas till</span><span class="sxs-lookup"><span data-stu-id="35e9a-154">**interface_index**: Index on which to get record</span></span>
- <span data-ttu-id="35e9a-155">**record_ptr**: pekare till posten DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-155">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-156">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-156">Return Values</span></span>

- <span data-ttu-id="35e9a-157">**NX_SUCCESS (0x0)**: klient posten har skapats</span><span class="sxs-lookup"><span data-stu-id="35e9a-157">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="35e9a-158">**NX_DHCP_NOT_BOUND**: (0X94) **klienten är inte i ett begränsat tillstånd**</span><span class="sxs-lookup"><span data-stu-id="35e9a-158">**NX_DHCP_NOT_BOUND**: (0x94) **Client not in Bound state**</span></span>
- <span data-ttu-id="35e9a-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0X9A) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="35e9a-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="35e9a-160">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="35e9a-160">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="35e9a-161">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="35e9a-161">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-162">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-162">Allowed From</span></span>

<span data-ttu-id="35e9a-163">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-164">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="35e9a-165">nx_dhcp_ client_restore_record</span><span class="sxs-lookup"><span data-stu-id="35e9a-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="35e9a-166">Återställa DHCP-klienten från en tidigare sparad post</span><span class="sxs-lookup"><span data-stu-id="35e9a-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-167">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-167">Prototype</span></span>

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a><span data-ttu-id="35e9a-168">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-168">Description</span></span>

<span data-ttu-id="35e9a-169">Den här tjänsten gör det möjligt för ett program att återställa sin DHCP-klient från en tidigare session med hjälp av DHCP-klienttjänsten som record_ptr.</span><span class="sxs-lookup"><span data-stu-id="35e9a-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="35e9a-170">Time_elapsed-indatatypen används för den tid som återstår på DHCP-klientens lån.</span><span class="sxs-lookup"><span data-stu-id="35e9a-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="35e9a-171">Detta kräver att DHCP-klientprogrammet skapar en post för DHCP-klienten innan den stängs av och sparar posten till ett beständigt minne.</span><span class="sxs-lookup"><span data-stu-id="35e9a-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="35e9a-172">Om fler än ett gränssnitt är aktiverat för DHCP-klienten, tillämpas den här tjänsten på det första giltiga gränssnittet som finns i DHCP-klientens instans.</span><span class="sxs-lookup"><span data-stu-id="35e9a-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-173">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-173">Input Parameters</span></span>

- <span data-ttu-id="35e9a-174">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-174">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="35e9a-175">**record_ptr**: pekare till posten DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-175">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="35e9a-176">**time_elapsed**: tid för att ta bort från den återstående låne tiden i posten för indata-klienten</span><span class="sxs-lookup"><span data-stu-id="35e9a-176">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-177">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-177">Return Values</span></span>

- <span data-ttu-id="35e9a-178">**NX_SUCCESS**: (0x0)-klient posten har återställts</span><span class="sxs-lookup"><span data-stu-id="35e9a-178">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="35e9a-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) inga gränssnitt som kör DHCP</span><span class="sxs-lookup"><span data-stu-id="35e9a-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces running DHCP</span></span>
- <span data-ttu-id="35e9a-180">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="35e9a-180">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-181">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-181">Allowed From</span></span>

<span data-ttu-id="35e9a-182">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-183">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-183">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="35e9a-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="35e9a-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="35e9a-185">Återställa DHCP-klienten från en tidigare sparad post på ett visst gränssnitt</span><span class="sxs-lookup"><span data-stu-id="35e9a-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-186">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-186">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="35e9a-187">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-187">Description</span></span>

<span data-ttu-id="35e9a-188">Den här tjänsten gör det möjligt för ett program att återställa DHCP-klienten på det angivna gränssnittet med hjälp av DHCP-klienttjänsten som record_ptr.</span><span class="sxs-lookup"><span data-stu-id="35e9a-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="35e9a-189">Time_elapsed-indatatypen används för den tid som återstår på DHCP-klientens lån.</span><span class="sxs-lookup"><span data-stu-id="35e9a-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="35e9a-190">Detta kräver att DHCP-klientprogrammet skapar en post för DHCP-klienten innan den stängs av och sparar posten till ett beständigt minne.</span><span class="sxs-lookup"><span data-stu-id="35e9a-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="35e9a-191">Om fler än ett gränssnitt är aktiverat för DHCP-klienten, tillämpas den här tjänsten på det första giltiga gränssnittet som finns i DHCP-klientens instans.</span><span class="sxs-lookup"><span data-stu-id="35e9a-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-192">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-192">Input Parameters</span></span>

- <span data-ttu-id="35e9a-193">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-193">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="35e9a-194">**record_ptr**: pekare till posten DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-194">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="35e9a-195">**time_elapsed**: tid för att ta bort från den återstående låne tiden i posten för indata-klienten</span><span class="sxs-lookup"><span data-stu-id="35e9a-195">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-196">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-196">Return Values</span></span>

- <span data-ttu-id="35e9a-197">**NX_SUCCESS**: (0x0)-klient posten har återställts</span><span class="sxs-lookup"><span data-stu-id="35e9a-197">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="35e9a-198">**NX_DHCP_NOT_BOUND**: (0X94) klienten är inte kopplad till IP-adressen</span><span class="sxs-lookup"><span data-stu-id="35e9a-198">**NX_DHCP_NOT_BOUND**: (0x94) Client not bound to IP address</span></span>
- <span data-ttu-id="35e9a-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0X9A) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="35e9a-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="35e9a-200">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="35e9a-200">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="35e9a-201">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="35e9a-201">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-202">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-202">Allowed From</span></span>

<span data-ttu-id="35e9a-203">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-204">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-204">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="35e9a-205">nx_dhcp_ client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="35e9a-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="35e9a-206">Uppdatera tiden kvar på DHCP-klientens lån</span><span class="sxs-lookup"><span data-stu-id="35e9a-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-207">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-207">Prototype</span></span>

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="35e9a-208">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-208">Description</span></span>

<span data-ttu-id="35e9a-209">Den här tjänsten uppdaterar den tid som återstår på DHCP-klientens IP-adresslån med time_elapsed indata för det första gränssnittet som har Aktiver ATS för DHCP som finns på DHCP-klientens instans.</span><span class="sxs-lookup"><span data-stu-id="35e9a-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="35e9a-210">Programmet måste pausa klient tråden för DHCP innan du använder den här tjänsten med hjälp av *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="35e9a-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="35e9a-211">När den här tjänsten har anropats kan programmet återuppta DHCP-klient tråden genom att anropa *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="35e9a-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="35e9a-212">Detta är avsett för DHCP-klientprogram som behöver pausa DHCP-klientens tråd under en viss tids period och sedan uppdatera IP-adressens låne tid kvar.</span><span class="sxs-lookup"><span data-stu-id="35e9a-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="35e9a-213">OBS! den här tjänsten är inte avsedd att användas med *nx_dhcp_client_get_record* och *nx_dhcp_client_restore_record* som beskrivs ovan).</span><span class="sxs-lookup"><span data-stu-id="35e9a-213">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="35e9a-214">Dessa tjänster beskrivs tidigare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="35e9a-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-215">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-215">Input Parameters</span></span>

- <span data-ttu-id="35e9a-216">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-216">**dhcp_ptr**: Pointer to DHCP Client</span></span> 
- <span data-ttu-id="35e9a-217">**time_elapsed**: tid att ta bort från den tid som återstår av IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="35e9a-217">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-218">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-218">Return Values</span></span>

- <span data-ttu-id="35e9a-219">**NX_SUCCESS**: (0x0) klientens IP-lån har uppdaterats</span><span class="sxs-lookup"><span data-stu-id="35e9a-219">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="35e9a-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) inga gränssnitt har Aktiver ATS för DHCP</span><span class="sxs-lookup"><span data-stu-id="35e9a-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="35e9a-221">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="35e9a-221">NX_PTR_ERROR: (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-222">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-222">Allowed From</span></span>

<span data-ttu-id="35e9a-223">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-224">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-224">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="35e9a-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="35e9a-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="35e9a-226">Uppdatera tiden kvar på DHCP-klientcertifikatet i det angivna gränssnittet</span><span class="sxs-lookup"><span data-stu-id="35e9a-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-227">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-227">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="35e9a-228">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-228">Description</span></span>

<span data-ttu-id="35e9a-229">Den här tjänsten uppdaterar den tid som återstår på DHCP-klientens IP-adresslån med time_elapsed indata på det angivna gränssnittet om gränssnittet är aktiverat för DHCP.</span><span class="sxs-lookup"><span data-stu-id="35e9a-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="35e9a-230">Programmet måste pausa klient tråden för DHCP innan du använder den här tjänsten med hjälp av *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="35e9a-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="35e9a-231">När den här tjänsten har anropats kan programmet återuppta DHCP-klient tråden genom att anropa *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="35e9a-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="35e9a-232">Obs! Om du pausar och återupptar återställningen av DHCP-klienten gäller alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="35e9a-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="35e9a-233">Detta är avsett för DHCP-klientprogram som behöver pausa DHCP-klientens tråd under en viss tids period och sedan uppdatera IP-adressens låne tid kvar.</span><span class="sxs-lookup"><span data-stu-id="35e9a-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="35e9a-234">OBS! den här tjänsten är inte avsedd att användas med *nx_dhcp_client_get_record* och *nx_dhcp_client_restore_record* som beskrivs ovan).</span><span class="sxs-lookup"><span data-stu-id="35e9a-234">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="35e9a-235">Dessa tjänster beskrivs tidigare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="35e9a-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-236">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-236">Input Parameters</span></span>

- <span data-ttu-id="35e9a-237">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-237">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="35e9a-238">**interface_index**: indexera till gränssnitt för att använda förfluten tid för att</span><span class="sxs-lookup"><span data-stu-id="35e9a-238">**interface_index**: Index to interface to apply elapsed time to</span></span>
- <span data-ttu-id="35e9a-239">**time_elapsed**: tid att ta bort från den tid som återstår av IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="35e9a-239">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-240">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-240">Return Values</span></span>

- <span data-ttu-id="35e9a-241">**NX_SUCCESS**: (0x0) klientens IP-lån har uppdaterats</span><span class="sxs-lookup"><span data-stu-id="35e9a-241">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="35e9a-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0X9A) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="35e9a-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="35e9a-243">NX_PTR_ERROR: (0x16) ogiltig DHCP-pekare.</span><span class="sxs-lookup"><span data-stu-id="35e9a-243">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="35e9a-244">NX_INVALID_INTERFACE: (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="35e9a-244">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-245">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-245">Allowed From</span></span>

<span data-ttu-id="35e9a-246">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-247">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-247">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a><span data-ttu-id="35e9a-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="35e9a-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="35e9a-249">Pausa klient tråden för DHCP</span><span class="sxs-lookup"><span data-stu-id="35e9a-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-250">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-250">Prototype</span></span>

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="35e9a-251">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-251">Description</span></span>

<span data-ttu-id="35e9a-252">Den här tjänsten pausar den aktuella DHCP-klient tråden.</span><span class="sxs-lookup"><span data-stu-id="35e9a-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="35e9a-253">Observera att till skillnad från *nx_dhcp_stop* sker ingen ändring av DHCP-klientens tillstånd när denna tjänst anropas.</span><span class="sxs-lookup"><span data-stu-id="35e9a-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="35e9a-254">Den här tjänsten inaktiverar DHCP som körs på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="35e9a-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="35e9a-255">Om du vill uppdatera DHCP-klientens tillstånd med förfluten tid medan DHCP-klienten har pausats, se den *nx_dhcp_client_update_time_remaining* som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="35e9a-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="35e9a-256">Om du vill återuppta en pausad DHCP-klient tråd bör programmet anropa *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="35e9a-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-257">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-257">Input Parameters</span></span>

- <span data-ttu-id="35e9a-258">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-258">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-259">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-259">Return Values</span></span>

- <span data-ttu-id="35e9a-260">**NX_SUCCESS**: (0x0) klient tråden har pausats</span><span class="sxs-lookup"><span data-stu-id="35e9a-260">**NX_SUCCESS**: (0x0) Client thread is suspended</span></span>
- <span data-ttu-id="35e9a-261">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="35e9a-261">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-262">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-262">Allowed From</span></span>

<span data-ttu-id="35e9a-263">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-264">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-264">Example</span></span>

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a><span data-ttu-id="35e9a-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="35e9a-265">nx_dhcp_resume</span></span>

<span data-ttu-id="35e9a-266">Återuppta en pausad DHCP-klient tråd</span><span class="sxs-lookup"><span data-stu-id="35e9a-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="35e9a-267">Prototyp</span><span class="sxs-lookup"><span data-stu-id="35e9a-267">Prototype</span></span>

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="35e9a-268">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="35e9a-268">Description</span></span>

<span data-ttu-id="35e9a-269">Den här tjänsten återupptar en pausad DHCP-klient tråd.</span><span class="sxs-lookup"><span data-stu-id="35e9a-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="35e9a-270">Observera att den faktiska statusen för DHCP-klienten inte ändras efter att klient tråden har återupptagits.</span><span class="sxs-lookup"><span data-stu-id="35e9a-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="35e9a-271">Om du vill uppdatera den återstående tiden i DHCP-klientens IP-adresslån med förfluten tid innan du anropar *nx_dhcp_resume*, se *nx_dhcp_client_update_time_remaining* som beskrivs ovan.</span><span class="sxs-lookup"><span data-stu-id="35e9a-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="35e9a-272">Den här tjänsten återupptar DHCP som körs på alla gränssnitt som är aktiverade för DHCP.</span><span class="sxs-lookup"><span data-stu-id="35e9a-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="35e9a-273">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="35e9a-273">Input Parameters</span></span>

- <span data-ttu-id="35e9a-274">**dhcp_ptr**: pekare till DHCP-klient</span><span class="sxs-lookup"><span data-stu-id="35e9a-274">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="35e9a-275">Retur värden</span><span class="sxs-lookup"><span data-stu-id="35e9a-275">Return Values</span></span>

- <span data-ttu-id="35e9a-276">**NX_SUCCESS**: (0x0) klient tråden har återupptagits</span><span class="sxs-lookup"><span data-stu-id="35e9a-276">**NX_SUCCESS**: (0x0) Client thread is resumed</span></span>
- <span data-ttu-id="35e9a-277">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="35e9a-277">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="35e9a-278">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="35e9a-278">Allowed From</span></span>

<span data-ttu-id="35e9a-279">Konversation</span><span class="sxs-lookup"><span data-stu-id="35e9a-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="35e9a-280">Exempel</span><span class="sxs-lookup"><span data-stu-id="35e9a-280">Example</span></span>

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```