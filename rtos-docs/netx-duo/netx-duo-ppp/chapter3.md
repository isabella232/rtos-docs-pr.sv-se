---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Point-to-Point Protocol-tjänster (PPP)
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo PPP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825824"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a><span data-ttu-id="77aff-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Point-to-Point Protocol-tjänster (PPP)</span><span class="sxs-lookup"><span data-stu-id="77aff-103">Chapter 3 - Description of Azure RTOS NetX Duo Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="77aff-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo PPP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="77aff-104">This chapter contains a description of all Azure RTOS NetX Duo PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="77aff-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="77aff-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="77aff-106">**nx_ppp_byte_receive**: *ta emot en byte från serie-ISR*</span><span class="sxs-lookup"><span data-stu-id="77aff-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="77aff-107">**nx_ppp_chap_challenge**: *skapa en CHAP-utmaning*</span><span class="sxs-lookup"><span data-stu-id="77aff-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="77aff-108">**nx_ppp_chap_enable**: *Aktivera CHAP-autentisering*</span><span class="sxs-lookup"><span data-stu-id="77aff-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="77aff-109">**nx_ppp_create**: *skapa en PPP-instans*</span><span class="sxs-lookup"><span data-stu-id="77aff-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="77aff-110">**nx_ppp_delete**: *ta bort en PPP-instans*</span><span class="sxs-lookup"><span data-stu-id="77aff-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="77aff-111">**nx_ppp_dns_address_get**: *Hämta DNS-serverns IP-adress*</span><span class="sxs-lookup"><span data-stu-id="77aff-111">**nx_ppp_dns_address_get**: *Get DNS Server IP address*</span></span>
- <span data-ttu-id="77aff-112">**nx_ppp_dns_address_set**:*Ange DNS-serverns IP-adress*</span><span class="sxs-lookup"><span data-stu-id="77aff-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="77aff-113">**nx_ppp_secondary_dns_address_get**: *Hämta IP-adress för sekundär DNS-Server*</span><span class="sxs-lookup"><span data-stu-id="77aff-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="77aff-114">**nx_ppp_secondary_dns_address_set**: *Ange IP-adress för Secondary_DNS Server*</span><span class="sxs-lookup"><span data-stu-id="77aff-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="77aff-115">**nx_ppp_interface_index_get**: *Hämta IP-gränssnitts index*</span><span class="sxs-lookup"><span data-stu-id="77aff-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="77aff-116">**nx_ppp_ip_address_assign**: *tilldela IP-adresser för IPCP*</span><span class="sxs-lookup"><span data-stu-id="77aff-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="77aff-117">**nx_ppp_link_down_notify**: *meddela programmet vid en länk*</span><span class="sxs-lookup"><span data-stu-id="77aff-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="77aff-118">**nx_ppp_link_up_notify**: *meddela programmet vid länkning*</span><span class="sxs-lookup"><span data-stu-id="77aff-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="77aff-119">**nx_ppp_nak_authentication_notify**: *meddela program om autentiserings-NAK tas emot*</span><span class="sxs-lookup"><span data-stu-id="77aff-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="77aff-120">**nx_ppp_pap_enable**: *aktivera PAP-autentisering*</span><span class="sxs-lookup"><span data-stu-id="77aff-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="77aff-121">**nx_ppp_ping_request**: *skicka en LCP ECHO-begäran*</span><span class="sxs-lookup"><span data-stu-id="77aff-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="77aff-122">**nx_ppp_raw_string_send**: *skicka icke-PPP-sträng*</span><span class="sxs-lookup"><span data-stu-id="77aff-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="77aff-123">**nx_ppp_restart**: *starta om PPP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="77aff-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="77aff-124">**nx_ppp_start**: *Starta PPP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="77aff-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="77aff-125">**nx_ppp_status_get**: *Hämta aktuell PPP-status*</span><span class="sxs-lookup"><span data-stu-id="77aff-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="77aff-126">**nx_ppp_stop**: *stoppa PPP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="77aff-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="77aff-127">**nx_ppp_packet_receive**: *ta emot PPP-paket*</span><span class="sxs-lookup"><span data-stu-id="77aff-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="77aff-128">**nx_ppp_packet_send_set**: *Konfigurera funktionen för att skicka PPP-paket*</span><span class="sxs-lookup"><span data-stu-id="77aff-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="77aff-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="77aff-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="77aff-130">Ta emot en byte från serie-ISR</span><span class="sxs-lookup"><span data-stu-id="77aff-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-131">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="77aff-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-132">Description</span></span>

<span data-ttu-id="77aff-133">Den här tjänsten anropas vanligt vis från programmets (ISR) driv rutin för seriell driv rutins tjänsten för att överföra mottagna byte till PPP.</span><span class="sxs-lookup"><span data-stu-id="77aff-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="77aff-134">Vid anrop placerar den här rutinen mottagna byte i en cirkelformad byte-buffert och meddelar lämplig PPP-tråd för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="77aff-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-135">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-135">Input Parameters</span></span>

- <span data-ttu-id="77aff-136">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-137">**byte**: byte mottaget från seriell enhet</span><span class="sxs-lookup"><span data-stu-id="77aff-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-138">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-138">Return Values</span></span>

- <span data-ttu-id="77aff-139">**NX_SUCCESS**: (0X00) lyckad PPP-byte-mottagning.</span><span class="sxs-lookup"><span data-stu-id="77aff-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="77aff-140">**NX_PPP_BUFFER_FULL**: (0XB1) PPP Serial buffer är redan full.</span><span class="sxs-lookup"><span data-stu-id="77aff-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="77aff-141">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-142">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-142">Allowed From</span></span>

<span data-ttu-id="77aff-143">Trådar, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-144">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="77aff-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="77aff-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="77aff-146">Generera en CHAP-utmaning</span><span class="sxs-lookup"><span data-stu-id="77aff-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-147">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-148">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-148">Description</span></span>

<span data-ttu-id="77aff-149">Den här tjänsten initierar en CHAP-utmaning när PPP-anslutningen redan är igång.</span><span class="sxs-lookup"><span data-stu-id="77aff-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="77aff-150">Detta ger programmet möjlighet att verifiera anslutningens äkthet på regelbunden basis.</span><span class="sxs-lookup"><span data-stu-id="77aff-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="77aff-151">Om utmaningen Miss lyckas stängs PPP-länken.</span><span class="sxs-lookup"><span data-stu-id="77aff-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-152">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-152">Input Parameters</span></span>

- <span data-ttu-id="77aff-153">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-154">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-154">Return Values</span></span>

- <span data-ttu-id="77aff-155">**NX_SUCCESS**: (0X00) lyckad PPP-utmaning har initierats.</span><span class="sxs-lookup"><span data-stu-id="77aff-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="77aff-156">**NX_PPP_FAILURE**: (0XB0) ogiltig PPP-utmaning. CHAP har bara Aktiver ATS för Response.</span><span class="sxs-lookup"><span data-stu-id="77aff-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="77aff-157">**NX_NOT_IMPLEMENTED**: (0X80) CHAP-logik har inaktiverats via NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="77aff-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="77aff-158">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="77aff-159">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-160">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-160">Allowed From</span></span>

<span data-ttu-id="77aff-161">Konversation</span><span class="sxs-lookup"><span data-stu-id="77aff-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-162">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="77aff-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="77aff-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="77aff-164">Aktivera CHAP-autentisering</span><span class="sxs-lookup"><span data-stu-id="77aff-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-165">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="77aff-166">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-166">Description</span></span>

<span data-ttu-id="77aff-167">Den här tjänsten aktiverar CHAP (Challenge-Handshake Authentication Protocol) för den angivna PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="77aff-168">Om funktions pekarna "\***get_challenge_values**_" och "_ \* _get_verification_values_\* \*" anges, krävs CHAP av den här PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="77aff-169">Annars svarar CHAP bara på motpartens utmanings begär Anden.</span><span class="sxs-lookup"><span data-stu-id="77aff-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="77aff-170">Det finns flera data objekt som refereras till nedan i de nödvändiga callback-funktionerna.</span><span class="sxs-lookup"><span data-stu-id="77aff-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="77aff-171">Data objektets *hemlighet*, *namn* och *system* förväntas vara null-terminerade strängar med en maximal storlek på NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="77aff-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="77aff-172">Data objekt *rand_value* förväntas vara en null-avslutad sträng med en maximal storlek på NX_PPP_VALUE_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="77aff-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="77aff-173">Dataobjektets *ID* är en enkel osignerad tecken typ.</span><span class="sxs-lookup"><span data-stu-id="77aff-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="77aff-174">Den här funktionen måste anropas efter *nx_ppp_create* men innan nx_ip_create eller *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="77aff-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-175">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-175">Input Parameters</span></span>

- <span data-ttu-id="77aff-176">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-177">**get_challenge_values**: pekare till program funktion för att hämta värden som används för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="77aff-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="77aff-178">Observera att värdena för *rand_value*, *ID* och *hemlighet* måste kopieras till de angivna målen.</span><span class="sxs-lookup"><span data-stu-id="77aff-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="77aff-179">**get_responder_values**: pekare till program funktion som hämtar värden som används för att svara på en utmaning.</span><span class="sxs-lookup"><span data-stu-id="77aff-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="77aff-180">Observera att värdena *system*, *Name* och *Secret* måste kopieras till de angivna målen.</span><span class="sxs-lookup"><span data-stu-id="77aff-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="77aff-181">**get_verification_values**: pekare till program funktion som hämtar värden som används för att verifiera utmanings svaret.</span><span class="sxs-lookup"><span data-stu-id="77aff-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="77aff-182">Observera att värdena *system*,*Name* och *Secret* måste kopieras till de angivna målen.</span><span class="sxs-lookup"><span data-stu-id="77aff-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-183">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-183">Return Values</span></span>

- <span data-ttu-id="77aff-184">**NX_SUCCESS**: (0X00) lyckades PPP CHAP Enable</span><span class="sxs-lookup"><span data-stu-id="77aff-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="77aff-185">**NX_NOT_IMPLEMENTED**: (0X80) CHAP-logik har inaktiverats via NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="77aff-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="77aff-186">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller callback-funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="77aff-187">Observera att om *get_challenge_values* har angetts måste även *get_verification_values* -funktionen anges.</span><span class="sxs-lookup"><span data-stu-id="77aff-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="77aff-188">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-189">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-189">Allowed From</span></span>

<span data-ttu-id="77aff-190">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-191">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="77aff-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="77aff-192">nx_ppp_create</span></span>

<span data-ttu-id="77aff-193">Skapa en PPP-instans</span><span class="sxs-lookup"><span data-stu-id="77aff-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-194">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="77aff-195">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-195">Description</span></span>

<span data-ttu-id="77aff-196">Den här tjänsten skapar en PPP-instans för den angivna NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-196">This service creates a PPP instance for the specified NetX IP instance.</span></span> <span data-ttu-id="77aff-197">Den här funktionen måste anropas innan NetX-IP-instansen skapas.</span><span class="sxs-lookup"><span data-stu-id="77aff-197">This function must be called prior to creating the NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="77aff-198">Det är vanligt vis en bra idé att skapa NetX IP-tråd med högre prioritet än PPP-Trådens prioritet.</span><span class="sxs-lookup"><span data-stu-id="77aff-198">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="77aff-199">Mer information om hur du anger prioritet för IP-tråd finns i *nx_ip_create* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-199">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-200">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-200">Input Parameters</span></span>

- <span data-ttu-id="77aff-201">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-201">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-202">**namn**: namnet på den här PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-202">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="77aff-203">**ip_ptr**: pekare till kontroll block för en icke-skapad IP-instans.</span><span class="sxs-lookup"><span data-stu-id="77aff-203">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="77aff-204">**stack_memory_ptr**: pekare för att starta PPP-trådens stack Area.</span><span class="sxs-lookup"><span data-stu-id="77aff-204">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="77aff-205">**stack_size**: storlek i byte i trådens stack.</span><span class="sxs-lookup"><span data-stu-id="77aff-205">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="77aff-206">**pool_ptr**: pekar mot standardpaket-poolen.</span><span class="sxs-lookup"><span data-stu-id="77aff-206">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="77aff-207">**thread_priority**: prioritet för interna PPP-trådar (1-31).</span><span class="sxs-lookup"><span data-stu-id="77aff-207">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="77aff-208">**ppp_invalid_packet_handler**: funktions pekare till program hanterare för alla icke-PPP-paket.</span><span class="sxs-lookup"><span data-stu-id="77aff-208">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="77aff-209">NetX PPP anropar vanligt vis den här rutinen under initieringen.</span><span class="sxs-lookup"><span data-stu-id="77aff-209">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="77aff-210">Det är här som programmet kan svara på modem kommandon eller i Windows XP. NetX PPP-applikationen kan initiera PPP genom att svara på "klient SERVER" till den första "klienten" som skickas av Windows XP.</span><span class="sxs-lookup"><span data-stu-id="77aff-210">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="77aff-211">**ppp_byte_send**: funktions pekare till programmets serie byte-utdata.</span><span class="sxs-lookup"><span data-stu-id="77aff-211">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="77aff-212">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-212">Return Values</span></span>

- <span data-ttu-id="77aff-213">**NX_SUCCESS**: (0X00) lyckad PPP-skapande.</span><span class="sxs-lookup"><span data-stu-id="77aff-213">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="77aff-214">NX_PTR_ERROR: (0x07) ogiltig PPP-, IP-eller byte-utmatnings funktion.</span><span class="sxs-lookup"><span data-stu-id="77aff-214">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="77aff-215">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-216">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-216">Allowed From</span></span>

<span data-ttu-id="77aff-217">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-217">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-218">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-218">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="77aff-219">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="77aff-219">nx_ppp_delete</span></span>

<span data-ttu-id="77aff-220">Ta bort en PPP-instans</span><span class="sxs-lookup"><span data-stu-id="77aff-220">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-221">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-221">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-222">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-222">Description</span></span>

<span data-ttu-id="77aff-223">Den här tjänsten tar bort den tidigare skapade PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-223">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-224">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-224">Input Parameters</span></span>

- <span data-ttu-id="77aff-225">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-225">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-226">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-226">Return Values</span></span>

- <span data-ttu-id="77aff-227">**NX_SUCCESS**: (0X00) lyckad PPP-borttagning.</span><span class="sxs-lookup"><span data-stu-id="77aff-227">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="77aff-228">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-228">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="77aff-229">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-229">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-230">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-230">Allowed From</span></span>

<span data-ttu-id="77aff-231">Konversation</span><span class="sxs-lookup"><span data-stu-id="77aff-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-232">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-232">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="77aff-233">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="77aff-233">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="77aff-234">Hämta IP-adress för DNS-Server</span><span class="sxs-lookup"><span data-stu-id="77aff-234">Get DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-235">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-235">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-236">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-236">Description</span></span>

<span data-ttu-id="77aff-237">Den här tjänsten hämtar DNS-IP-adressen som anges av peer-datorn i IPCP-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="77aff-237">This service retrieves the DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="77aff-238">Om ingen IP-adress angavs av peer-datorn returneras en IP-adress på 0.</span><span class="sxs-lookup"><span data-stu-id="77aff-238">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-239">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-239">Input Parameters</span></span>

- <span data-ttu-id="77aff-240">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-240">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-241">**dns_address_ptr**: målet för DNS-serveradressen</span><span class="sxs-lookup"><span data-stu-id="77aff-241">**dns_address_ptr**: Destination for DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-242">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-242">Return Values</span></span>

- <span data-ttu-id="77aff-243">**NX_SUCCESS**: (0X00) lyckad DNS-adress Hämta.</span><span class="sxs-lookup"><span data-stu-id="77aff-243">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="77aff-244">**NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.</span><span class="sxs-lookup"><span data-stu-id="77aff-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="77aff-245">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-245">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-246">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-246">Allowed From</span></span>

<span data-ttu-id="77aff-247">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-247">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-248">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-248">Example</span></span>

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="77aff-249">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="77aff-249">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="77aff-250">Hämta IP-adress för sekundär DNS-Server</span><span class="sxs-lookup"><span data-stu-id="77aff-250">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-251">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-251">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-252">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-252">Description</span></span>

<span data-ttu-id="77aff-253">Den här tjänsten hämtar den sekundära DNS-IP-adressen som anges av peer-datorn i IPCP-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="77aff-253">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="77aff-254">Om ingen IP-adress angavs av peer-datorn returneras en IP-adress på 0.</span><span class="sxs-lookup"><span data-stu-id="77aff-254">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-255">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-255">Input Parameters</span></span>

- <span data-ttu-id="77aff-256">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-256">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-257">**dns_address_ptr**: mål för sekundär DNS-serveradress</span><span class="sxs-lookup"><span data-stu-id="77aff-257">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-258">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-258">Return Values</span></span>

- <span data-ttu-id="77aff-259">**NX_SUCCESS**: (0X00) lyckad DNS-adress Hämta.</span><span class="sxs-lookup"><span data-stu-id="77aff-259">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="77aff-260">**NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.</span><span class="sxs-lookup"><span data-stu-id="77aff-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="77aff-261">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-261">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-262">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-262">Allowed From</span></span>

<span data-ttu-id="77aff-263">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-263">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-264">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-264">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="77aff-265">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="77aff-265">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="77aff-266">Ange IP-adress för primär DNS-Server</span><span class="sxs-lookup"><span data-stu-id="77aff-266">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-267">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-267">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="77aff-268">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-268">Description</span></span>

<span data-ttu-id="77aff-269">Den här tjänsten anger IP-adressen för DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="77aff-269">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="77aff-270">Om peer-servern skickar en DNS-Server Option-begäran i IPCP-tillstånd, kommer den här värden att tillhandahålla informationen.</span><span class="sxs-lookup"><span data-stu-id="77aff-270">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-271">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-271">Input Parameters</span></span>

- <span data-ttu-id="77aff-272">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-272">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-273">**dns_address**: DNS-serveradress</span><span class="sxs-lookup"><span data-stu-id="77aff-273">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-274">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-274">Return Values</span></span>

- <span data-ttu-id="77aff-275">**NX_SUCCESS**: (0x00) en DNS-adress uppsättning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="77aff-275">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="77aff-276">**NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.</span><span class="sxs-lookup"><span data-stu-id="77aff-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="77aff-277">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-277">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-278">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-278">Allowed From</span></span>

<span data-ttu-id="77aff-279">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-279">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-280">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-280">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="77aff-281">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="77aff-281">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="77aff-282">Ange IP-adress för sekundär DNS-Server</span><span class="sxs-lookup"><span data-stu-id="77aff-282">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-283">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-283">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="77aff-284">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-284">Description</span></span>

<span data-ttu-id="77aff-285">Den här tjänsten anger IP-adressen för den sekundära DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="77aff-285">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="77aff-286">Om peer skickar en sekundär DNS-Server Options-begäran i IPCP-läget, kommer den här värden att tillhandahålla informationen.</span><span class="sxs-lookup"><span data-stu-id="77aff-286">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-287">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-287">Input Parameters</span></span>

- <span data-ttu-id="77aff-288">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-288">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-289">**dns_address**: sekundär DNS-serveradress</span><span class="sxs-lookup"><span data-stu-id="77aff-289">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-290">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-290">Return Values</span></span>

- <span data-ttu-id="77aff-291">**NX_SUCCESS**: (0x00) en DNS-adress uppsättning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="77aff-291">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="77aff-292">**NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.</span><span class="sxs-lookup"><span data-stu-id="77aff-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="77aff-293">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-293">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-294">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-294">Allowed From</span></span>

<span data-ttu-id="77aff-295">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-296">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-296">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="77aff-297">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="77aff-297">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="77aff-298">Hämta IP-gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="77aff-298">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-299">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-299">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-300">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-300">Description</span></span>

<span data-ttu-id="77aff-301">Den här tjänsten hämtar det IP-gränssnitts index som är associerat med denna PPP-instans.</span><span class="sxs-lookup"><span data-stu-id="77aff-301">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="77aff-302">Detta är endast användbart om PPP-instansen inte är det primära gränssnittet för en IP-instans.</span><span class="sxs-lookup"><span data-stu-id="77aff-302">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-303">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-303">Input Parameters</span></span>

- <span data-ttu-id="77aff-304">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-304">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-305">**index_ptr**: målet för gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="77aff-305">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-306">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-306">Return Values</span></span>

- <span data-ttu-id="77aff-307">**NX_SUCCESS**: (0X00) lyckades PPP-index Hämta.</span><span class="sxs-lookup"><span data-stu-id="77aff-307">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="77aff-308">**NX_IN_PROGRESS**: (0X37) PPP har inte slutfört initieringen.</span><span class="sxs-lookup"><span data-stu-id="77aff-308">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="77aff-309">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-309">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-310">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-310">Allowed From</span></span>

<span data-ttu-id="77aff-311">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-311">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-312">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-312">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="77aff-313">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="77aff-313">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="77aff-314">Tilldela IP-adresser för IPCP</span><span class="sxs-lookup"><span data-stu-id="77aff-314">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-315">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-315">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="77aff-316">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-316">Description</span></span>

<span data-ttu-id="77aff-317">Den här tjänsten konfigurerar lokala och peer-IP-adresser för användning i IPCP-protokollet (Internet Protocol Control Protocol).</span><span class="sxs-lookup"><span data-stu-id="77aff-317">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP.</span></span> <span data-ttu-id="77aff-318">Den ska anropas för PPP-instansen som har giltiga IP-adresser för sig och den andra peer-datorn.</span><span class="sxs-lookup"><span data-stu-id="77aff-318">It should be called for the PPP instance that has valid IP addresses for itself and the other peer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-319">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-319">Input Parameters</span></span>

- <span data-ttu-id="77aff-320">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-321">**local_ip_address**: lokal IP-adress.</span><span class="sxs-lookup"><span data-stu-id="77aff-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="77aff-322">**peer_ip_address**: peer-datorns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="77aff-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-323">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-323">Return Values</span></span>

- <span data-ttu-id="77aff-324">**NX_SUCCESS**: (0X00) slutförde PPP-adresstilldelning.</span><span class="sxs-lookup"><span data-stu-id="77aff-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="77aff-325">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="77aff-326">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-327">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-327">Allowed From</span></span>

<span data-ttu-id="77aff-328">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-329">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="77aff-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="77aff-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="77aff-331">Meddela programmet vid en länk</span><span class="sxs-lookup"><span data-stu-id="77aff-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-332">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="77aff-333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-333">Description</span></span>

<span data-ttu-id="77aff-334">Den här tjänsten registrerar programmets länk ned meddelande återanrop med den angivna PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="77aff-335">Om det inte är NULL anropas programmets länk ned callback-funktion när länken slutar fungera.</span><span class="sxs-lookup"><span data-stu-id="77aff-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-336">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-336">Input Parameters</span></span>

- <span data-ttu-id="77aff-337">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-338">**link_down_callback**: program varans länk ned meddelande funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="77aff-339">Om det här värdet är NULL inaktive ras länk ned meddelande.</span><span class="sxs-lookup"><span data-stu-id="77aff-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-340">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-340">Return Values</span></span>

- <span data-ttu-id="77aff-341">**NX_SUCCESS**: (0X00) slutförd länk för att registrera meddelande återanrop.</span><span class="sxs-lookup"><span data-stu-id="77aff-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="77aff-342">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-343">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-343">Allowed From</span></span>

<span data-ttu-id="77aff-344">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-345">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="77aff-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="77aff-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="77aff-347">Avisera program vid länkning</span><span class="sxs-lookup"><span data-stu-id="77aff-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-348">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="77aff-349">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-349">Description</span></span>

<span data-ttu-id="77aff-350">Den här tjänsten registrerar programmets länk upp ett meddelande återanrop med den angivna PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="77aff-351">Om det inte är NULL anropas programmets länk för motringning när länken visas.</span><span class="sxs-lookup"><span data-stu-id="77aff-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-352">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-352">Input Parameters</span></span>

- <span data-ttu-id="77aff-353">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-354">**link_up_callback**: programmets länk för meddelande funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="77aff-355">Om det här värdet är NULL är länkat meddelande inaktiverat. \* \*</span><span class="sxs-lookup"><span data-stu-id="77aff-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-356">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-356">Return Values</span></span>

- <span data-ttu-id="77aff-357">**NX_SUCCESS**: (0x00) länkad registrering av meddelande återanrop.</span><span class="sxs-lookup"><span data-stu-id="77aff-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="77aff-358">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-359">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-359">Allowed From</span></span>

<span data-ttu-id="77aff-360">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-361">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="77aff-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="77aff-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="77aff-363">Meddela program om autentisering NAK tas emot</span><span class="sxs-lookup"><span data-stu-id="77aff-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-364">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="77aff-365">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-365">Description</span></span>

<span data-ttu-id="77aff-366">Den här tjänsten registrerar programmets autentiserings-NAK meddelande återanrop med den angivna PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="77aff-367">Om den inte är NULL anropas den här återanrops funktionen när PPP-instansen får en NAK under authentiaction.</span><span class="sxs-lookup"><span data-stu-id="77aff-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-368">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-368">Input Parameters</span></span>

- <span data-ttu-id="77aff-369">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-370">**nak_authentication_notify**: pekare till funktion som anropas när PPP-instansen får en autentiserings-NAK.</span><span class="sxs-lookup"><span data-stu-id="77aff-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="77aff-371">Om värdet är NULL är meddelandet inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="77aff-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-372">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-372">Return Values</span></span>

- <span data-ttu-id="77aff-373">**NX_SUCCESS**: (0x00) registreringen av återanrop i meddelande lyckades.</span><span class="sxs-lookup"><span data-stu-id="77aff-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="77aff-374">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-375">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-375">Allowed From</span></span>

<span data-ttu-id="77aff-376">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-377">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="77aff-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="77aff-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="77aff-379">Aktivera PAP-autentisering</span><span class="sxs-lookup"><span data-stu-id="77aff-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-380">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="77aff-381">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-381">Description</span></span>

<span data-ttu-id="77aff-382">Den här tjänsten aktiverar PAP-protokollet (Password Authentication Protocol) för den angivna PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="77aff-383">Om funktions pekaren "***verify_login***" anges krävs PAP av den här PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="77aff-384">Annars svarar PAP endast på motpartens PAP-krav som anges under LCP-förhandlingen.</span><span class="sxs-lookup"><span data-stu-id="77aff-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="77aff-385">Det finns flera data objekt som refereras till nedan i de nödvändiga callback-funktionerna.</span><span class="sxs-lookup"><span data-stu-id="77aff-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="77aff-386">Data objektets *namn* förväntas vara null-avslutad sträng med en maximal storlek på NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="77aff-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="77aff-387">*Lösen ordet* för data objekt förväntas också vara en null-avslutad sträng med en maximal storlek på NX_PPP_PASSWORD_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="77aff-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="77aff-388">Den här funktionen måste anropas efter *nx_ppp_create* men innan *nx_ip_create* eller *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="77aff-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-389">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-389">Input Parameters</span></span>

- <span data-ttu-id="77aff-390">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-391">**generate_login**: pekare till program funktion som skapar ett *namn* och *lösen ord* för autentisering av peer-datorn.</span><span class="sxs-lookup"><span data-stu-id="77aff-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="77aff-392">Observera att värdena för *namn* och *lösen ord* måste kopieras till de angivna målen.</span><span class="sxs-lookup"><span data-stu-id="77aff-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="77aff-393">**verify_login**: pekare till program funktion som verifierar det *namn* och *lösen ord* som anges av peer-datorn.</span><span class="sxs-lookup"><span data-stu-id="77aff-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="77aff-394">Den här rutinen måste jämföra det angivna *namnet* och *lösen ordet*.</span><span class="sxs-lookup"><span data-stu-id="77aff-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="77aff-395">Om den här rutinen returnerar NX_SUCCESS är namnet och lösen ordet rätt och PPP kan fortsätta till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="77aff-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="77aff-396">Annars returnerar den här rutinen NX_PPP_ERROR och PPP bara väntar på ett annat namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="77aff-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-397">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-397">Return Values</span></span>

- <span data-ttu-id="77aff-398">**NX_SUCCESS**: (0X00) SLUTFÖRDE PPP PAP enable.</span><span class="sxs-lookup"><span data-stu-id="77aff-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="77aff-399">**NX_NOT_IMPLEMENTED**: (0X80) PAP-logiken inaktiverades via NX_PPP_DISABLE_PAP.</span><span class="sxs-lookup"><span data-stu-id="77aff-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="77aff-400">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller program funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="77aff-401">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-402">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-402">Allowed From</span></span>

<span data-ttu-id="77aff-403">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-404">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="77aff-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="77aff-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="77aff-406">Skicka en LCP ping-begäran</span><span class="sxs-lookup"><span data-stu-id="77aff-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-407">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="77aff-408">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-408">Description</span></span>

<span data-ttu-id="77aff-409">Den här tjänsten skickar en LCP-begäran och anger en flagga som PPP-enheten väntar på ett eko svar.</span><span class="sxs-lookup"><span data-stu-id="77aff-409">This service sends an LCP request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="77aff-410">Alternativet vänta är primärt för *nx_packet_allocate* -anropet.</span><span class="sxs-lookup"><span data-stu-id="77aff-410">The wait option is primarily for the *nx_packet_allocate* call.</span></span> <span data-ttu-id="77aff-411">Tjänsten returnerar så fort begäran skickas.</span><span class="sxs-lookup"><span data-stu-id="77aff-411">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="77aff-412">Det väntar inte på svar.</span><span class="sxs-lookup"><span data-stu-id="77aff-412">It does not wait for a response.</span></span> 

<span data-ttu-id="77aff-413">När ett matchande eko svar tas emot, tar PPP-trådens aktivitet bort flaggan.</span><span class="sxs-lookup"><span data-stu-id="77aff-413">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="77aff-414">PPP-enheten måste ha slutfört LCP-delen av PPP-förhandlingen.</span><span class="sxs-lookup"><span data-stu-id="77aff-414">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="77aff-415">Den här tjänsten är användbar för PPP-konfiguration där det inte går att avsöka maskin vara för länk status.</span><span class="sxs-lookup"><span data-stu-id="77aff-415">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-416">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-416">Input Parameters</span></span>

- <span data-ttu-id="77aff-417">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-417">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-418">**data**: pekare till data som ska skickas i ekobegäran.</span><span class="sxs-lookup"><span data-stu-id="77aff-418">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="77aff-419">**data_size**: storleken på de data som ska skickas wait_option tid att vänta på att skicka LCP-eko meddelandet.</span><span class="sxs-lookup"><span data-stu-id="77aff-419">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-420">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-420">Return Values</span></span>

- <span data-ttu-id="77aff-421">**NX_SUCCESS**: (0X00) lyckad begäran om ekobegäran.</span><span class="sxs-lookup"><span data-stu-id="77aff-421">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="77aff-422">**NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP-anslutningen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="77aff-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="77aff-423">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller program funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-423">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="77aff-424">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-424">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-425">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-425">Allowed From</span></span>

<span data-ttu-id="77aff-426">Program trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-426">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-427">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-427">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="77aff-428">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="77aff-428">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="77aff-429">Skicka en RAW ASCII-sträng</span><span class="sxs-lookup"><span data-stu-id="77aff-429">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-430">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-430">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-431">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-431">Description</span></span>

<span data-ttu-id="77aff-432">Den här tjänsten skickar en icke-PPP ASCII-sträng direkt ut PPP-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="77aff-432">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="77aff-433">Den används vanligt vis när PPP får ett icke-PPP-paket som innehåller information om modem kontroll.</span><span class="sxs-lookup"><span data-stu-id="77aff-433">It is typically used after PPP receives an non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-434">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-434">Input Parameters</span></span>

- <span data-ttu-id="77aff-435">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-435">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-436">**string_ptr**: pekare till sträng som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="77aff-436">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-437">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-437">Return Values</span></span>

- <span data-ttu-id="77aff-438">**NX_SUCCESS**: (0X00) lyckad PPP RAW-sträng skicka.</span><span class="sxs-lookup"><span data-stu-id="77aff-438">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="77aff-439">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller sträng pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-439">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="77aff-440">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-440">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-441">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-441">Allowed From</span></span>

<span data-ttu-id="77aff-442">Konversation</span><span class="sxs-lookup"><span data-stu-id="77aff-442">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-443">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-443">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="77aff-444">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="77aff-444">nx_ppp_restart</span></span>

<span data-ttu-id="77aff-445">Starta om PPP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="77aff-445">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-446">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-446">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-447">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-447">Description</span></span>

<span data-ttu-id="77aff-448">Den här tjänsten startar om PPP-bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="77aff-448">This service restarts the PPP processing.</span></span> <span data-ttu-id="77aff-449">Det kallas vanligt vis när länken måste upprättas igen antingen från en länk ned motringning eller av ett modem som inte är ett PPP-meddelande som anger att kommunikationen bröts.</span><span class="sxs-lookup"><span data-stu-id="77aff-449">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-450">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-450">Input Parameters</span></span>

- <span data-ttu-id="77aff-451">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-451">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-452">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-452">Return Values</span></span>

- <span data-ttu-id="77aff-453">**NX_SUCCESS**: (0X00) lyckad PPP-omstart initierad.</span><span class="sxs-lookup"><span data-stu-id="77aff-453">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="77aff-454">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-454">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="77aff-455">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-455">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-456">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-456">Allowed From</span></span>

<span data-ttu-id="77aff-457">Konversation</span><span class="sxs-lookup"><span data-stu-id="77aff-457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-458">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-458">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="77aff-459">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="77aff-459">nx_ppp_start</span></span>

<span data-ttu-id="77aff-460">Starta PPP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="77aff-460">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-461">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-461">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-462">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-462">Description</span></span>

<span data-ttu-id="77aff-463">Den här tjänsten startar PPP-bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="77aff-463">This service starts the PPP processing.</span></span> <span data-ttu-id="77aff-464">Den anropas vanligt vis efter att nx_ppp_stop () anropades.</span><span class="sxs-lookup"><span data-stu-id="77aff-464">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="77aff-465">PPP startar automatiskt PPP-bearbetningen när länken är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="77aff-465">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-466">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-466">Input Parameters</span></span>

- <span data-ttu-id="77aff-467">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-467">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-468">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-468">Return Values</span></span>

- <span data-ttu-id="77aff-469">**NX_SUCCESS**: (0x00) en lyckad PPP-start har initierats.</span><span class="sxs-lookup"><span data-stu-id="77aff-469">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="77aff-470">**NX_PPP_ALREADY_STARTED**: (0XB9) PPP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="77aff-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="77aff-471">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-471">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="77aff-472">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-472">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-473">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-473">Allowed From</span></span>

<span data-ttu-id="77aff-474">Konversation</span><span class="sxs-lookup"><span data-stu-id="77aff-474">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-475">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-475">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="77aff-476">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="77aff-476">nx_ppp_status_get</span></span>

<span data-ttu-id="77aff-477">Hämta aktuell PPP-status</span><span class="sxs-lookup"><span data-stu-id="77aff-477">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-478">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-478">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="77aff-479">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-479">Description</span></span>

<span data-ttu-id="77aff-480">Den här tjänsten hämtar aktuell status för den angivna PPP-instansen.</span><span class="sxs-lookup"><span data-stu-id="77aff-480">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-481">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-481">Input Parameters</span></span>

- <span data-ttu-id="77aff-482">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-482">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-483">**status_ptr**: målet för PPP-statusen är följande möjliga status värden:</span><span class="sxs-lookup"><span data-stu-id="77aff-483">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="77aff-484">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="77aff-484">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="77aff-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="77aff-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="77aff-486">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="77aff-486">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="77aff-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="77aff-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="77aff-488">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="77aff-488">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="77aff-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="77aff-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="77aff-490">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="77aff-490">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="77aff-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="77aff-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="77aff-492">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="77aff-492">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="77aff-493">Statusen är bara giltig om API: et returnerar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="77aff-493">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="77aff-494">Om något av värdena för \* _FAILED returneras, stoppas dessutom PPP-bearbetningen tills det startas om igen av programmet.</span><span class="sxs-lookup"><span data-stu-id="77aff-494">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-495">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-495">Return Values</span></span>

- <span data-ttu-id="77aff-496">**NX_SUCCESS**: (0X00) lyckad PPP-status-begäran.</span><span class="sxs-lookup"><span data-stu-id="77aff-496">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="77aff-497">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-497">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-498">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-498">Allowed From</span></span>

<span data-ttu-id="77aff-499">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="77aff-499">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="77aff-500">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-500">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="77aff-501">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="77aff-501">nx_ppp_stop</span></span>

<span data-ttu-id="77aff-502">Starta PPP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="77aff-502">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-503">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-503">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="77aff-504">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-504">Description</span></span>

<span data-ttu-id="77aff-505">Den här tjänsten stoppar PPP-bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="77aff-505">This service stops the PPP processing.</span></span> <span data-ttu-id="77aff-506">Användaren kan också anropa nx_ppp_start () för att starta PPP-bearbetningen om det behövs.</span><span class="sxs-lookup"><span data-stu-id="77aff-506">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-507">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-507">Input Parameters</span></span>

- <span data-ttu-id="77aff-508">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-508">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-509">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-509">Return Values</span></span>

- <span data-ttu-id="77aff-510">**NX_SUCCESS**: (0x00) en lyckad PPP-start har initierats.</span><span class="sxs-lookup"><span data-stu-id="77aff-510">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="77aff-511">**NX_PPP_ALREADY_STOPPED**: (0XB8) PPP har redan stoppats.</span><span class="sxs-lookup"><span data-stu-id="77aff-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="77aff-512">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-512">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="77aff-513">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="77aff-513">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-514">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-514">Allowed From</span></span>

<span data-ttu-id="77aff-515">Konversation</span><span class="sxs-lookup"><span data-stu-id="77aff-515">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-516">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-516">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="77aff-517">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="77aff-517">nx_ppp_packet_receive</span></span>

<span data-ttu-id="77aff-518">Ta emot PPP-paket</span><span class="sxs-lookup"><span data-stu-id="77aff-518">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-519">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-519">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="77aff-520">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-520">Description</span></span>

<span data-ttu-id="77aff-521">Den här tjänsten tar emot PPP-paket.</span><span class="sxs-lookup"><span data-stu-id="77aff-521">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-522">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-522">Input Parameters</span></span>

- <span data-ttu-id="77aff-523">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-523">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-524">**packet_ptr**: pekar mot PPP-paket.</span><span class="sxs-lookup"><span data-stu-id="77aff-524">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-525">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-525">Return Values</span></span>

- <span data-ttu-id="77aff-526">**NX_SUCCESS**: (0X00) lyckad PPP-status-begäran.</span><span class="sxs-lookup"><span data-stu-id="77aff-526">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="77aff-527">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-527">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-528">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-528">Allowed From</span></span>

<span data-ttu-id="77aff-529">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-529">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-530">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-530">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="77aff-531">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="77aff-531">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="77aff-532">Ange funktionen Skicka PPP-paket</span><span class="sxs-lookup"><span data-stu-id="77aff-532">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="77aff-533">Prototyp</span><span class="sxs-lookup"><span data-stu-id="77aff-533">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="77aff-534">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77aff-534">Description</span></span>

<span data-ttu-id="77aff-535">Den här tjänsten anger PPP-paketets sändnings-funciton.</span><span class="sxs-lookup"><span data-stu-id="77aff-535">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77aff-536">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="77aff-536">Input Parameters</span></span>

- <span data-ttu-id="77aff-537">**ppp_ptr**: pekar mot PPP-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="77aff-537">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="77aff-538">**nx_ppp_packet_send**: rutin för att skicka PPP-paket.</span><span class="sxs-lookup"><span data-stu-id="77aff-538">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="77aff-539">Retur värden</span><span class="sxs-lookup"><span data-stu-id="77aff-539">Return Values</span></span>

- <span data-ttu-id="77aff-540">**NX_SUCCESS**: (0X00) lyckad PPP-status-begäran.</span><span class="sxs-lookup"><span data-stu-id="77aff-540">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="77aff-541">NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.</span><span class="sxs-lookup"><span data-stu-id="77aff-541">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77aff-542">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="77aff-542">Allowed From</span></span>

<span data-ttu-id="77aff-543">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="77aff-543">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="77aff-544">Exempel</span><span class="sxs-lookup"><span data-stu-id="77aff-544">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```