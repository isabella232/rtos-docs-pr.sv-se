---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX LWM2M Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX LWM2M-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826673"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="33f75-103">Kapitel 4 – Beskrivning av Azure återställnings tider NetX LWM2M Services</span><span class="sxs-lookup"><span data-stu-id="33f75-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="33f75-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX LWM2M-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="33f75-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="33f75-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="33f75-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="33f75-106">LWM2M klient hantering</span><span class="sxs-lookup"><span data-stu-id="33f75-106">LWM2M Client Management</span></span>

- <span data-ttu-id="33f75-107">**nx_lwm2m_client_create**: *skapa lwm2m-klient*</span><span class="sxs-lookup"><span data-stu-id="33f75-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="33f75-108">**nx_lwm2m_client_delete**: *ta bort lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="33f75-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="33f75-109">**nx_lwm2m_client_lock**: *Lås lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="33f75-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="33f75-110">**nx_lwm2m_client_object_add**: *Lägg till objekt implementering i lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="33f75-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="33f75-111">**nx_lwm2m_client_unlock**: *Lås upp lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="33f75-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="33f75-112">LWM2M för hantering av klient</span><span class="sxs-lookup"><span data-stu-id="33f75-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="33f75-113">**nx_lwm2m_client_session_bootstrap**: *starta en session med en Start Server*</span><span class="sxs-lookup"><span data-stu-id="33f75-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="33f75-114">**nx_lwm2m_client_session_bootstrap_dtls**: *starta en säker session med en Start Server*</span><span class="sxs-lookup"><span data-stu-id="33f75-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="33f75-115">**nx_lwm2m_client_session_create**: *skapa en lwm2m-klientsession*</span><span class="sxs-lookup"><span data-stu-id="33f75-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="33f75-116">**nx_lwm2m_client_session_delete**: *ta bort lwm2m-klientsession*</span><span class="sxs-lookup"><span data-stu-id="33f75-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="33f75-117">**nx_lwm2m_client_session_deregister**: *Avsluta en session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="33f75-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="33f75-118">**nx_lwm2m_client_session_error_get**: *Hämta senaste fel i en session*</span><span class="sxs-lookup"><span data-stu-id="33f75-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="33f75-119">**nx_lwm2m_client_session_register**: *starta en session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="33f75-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="33f75-120">**nx_lwm2m_client_session_register_dtls**: *starta en säker session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="33f75-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="33f75-121">**nx_lwm2m_client_session_update**: *Uppdatera en session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="33f75-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="33f75-122">Implementering av säkerhets objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-122">Security Object Implementation</span></span>

- <span data-ttu-id="33f75-123">**nx_lwm2m_client_security_key_callbacks_set**: *Ange återanrop för hantering av säkerhets nycklar*</span><span class="sxs-lookup"><span data-stu-id="33f75-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="33f75-124">Implementering av enhets objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-124">Device Object Implementation</span></span>

- <span data-ttu-id="33f75-125">**nx_lwm2m_client_device_callbacks_set**: *Ange återanrop i enhets objekts program*</span><span class="sxs-lookup"><span data-stu-id="33f75-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="33f75-126">**nx_lwm2m_client_device_error_push**: *Lägg till felkod till enhets objekt*</span><span class="sxs-lookup"><span data-stu-id="33f75-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="33f75-127">**nx_lwm2m_client_device_error_reset**: *återställa felkoder för enhets objekt*</span><span class="sxs-lookup"><span data-stu-id="33f75-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="33f75-128">**nx_lwm2m_client_device_resource_changed**: *signal ändring av enhets objekt resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="33f75-129">Implementering av anpassade objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="33f75-130">**nx_lwm2m_object_resource_changed**: *signal ändring av ett resurs värde för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="33f75-131">Hantering av lokala enheter</span><span class="sxs-lookup"><span data-stu-id="33f75-131">Local Device Management</span></span>

- <span data-ttu-id="33f75-132">**nx_lwm2m_client_object_create**: *skapa en ny objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="33f75-133">**nx_lwm2m_client_object_delete**: *ta bort en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="33f75-134">**nx_lwm2m_client_object_discover**: *identifiera resurser för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="33f75-135">**nx_lwm2m_client_object_execute**: *Kör resurs för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="33f75-136">**nx_lwm2m_client_object_get_next**: *Hämta listan över objekt som IMPLEMENTERAs av lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="33f75-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="33f75-137">**nx_lwm2m_client_object_instance_get_next**: *Hämta listan över instanser av ett objekt*</span><span class="sxs-lookup"><span data-stu-id="33f75-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="33f75-138">**nx_lwm2m_client_object_read**: *läsa resurs värden för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="33f75-139">**nx_lwm2m_client_object_write**: *Ändra resurs värden för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="33f75-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="33f75-140">Resurs värden avkodning</span><span class="sxs-lookup"><span data-stu-id="33f75-140">Resources Values Decoding</span></span>

- <span data-ttu-id="33f75-141">**nx_lwm2m_resource_get_boolean**: *Hämta värdet för en boolesk resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="33f75-142">**nx_lwm2m_resource_get_float32**: *Hämta värdet för en 32-bitars svävande punkt resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="33f75-143">**nx_lwm2m_resource_get_float64**: *Hämta värdet för en 64-bitars svävande punkt resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="33f75-144">**nx_lwm2m_resource_get_integer32**: *Hämta värdet för en 32-bitars heltals resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="33f75-145">**nx_lwm2m_resource_get_integer64**: *Hämta värdet för en 64-bitars heltals resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="33f75-146">**nx_lwm2m_resource_get_objlnk**: *Hämta värdet för en objekt länk resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="33f75-147">**nx_lwm2m_resource_get_opaque**: *Hämta värdet för en ogenomskinlig resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="33f75-148">**nx_lwm2m_resource_get_string**: *Hämta värdet för en sträng resurs*</span><span class="sxs-lookup"><span data-stu-id="33f75-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="33f75-149">**nx_lwm2m_resource_multiple_get_boolean**: *Hämta värdet för en boolesk resurs flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-150">**nx_lwm2m_resource_multiple_get_float32**: *Hämta värdet för en 32-bitars flytt ALS plats med flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-151">**nx_lwm2m_resource_multiple_get_float64**: *Hämta värdet för en 64-bitars flytt ALS plats med flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-152">**nx_lwm2m_resource_multiple_get_integer32**: *Hämta värdet för ett 32-bitars heltal med flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-153">**nx_lwm2m_resource_multiple_get_integer64**: *Hämta värdet för ett 64-bitars heltal med flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Hämta värdet för en objekt länk flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-155">**nx_lwm2m_resource_multiple_get_opaque**: *Hämta värdet för en täckande flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="33f75-156">**nx_lwm2m_resource_multiple_get_string**: *Hämta värdet för en sträng flera resurs instanser*</span><span class="sxs-lookup"><span data-stu-id="33f75-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="33f75-157">Uppdaterings objekt för inbyggd program vara</span><span class="sxs-lookup"><span data-stu-id="33f75-157">Firmware Update Object</span></span>

- <span data-ttu-id="33f75-158">**nx_lwm2m_firmware_create**: *skapa uppdaterings objekt för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="33f75-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="33f75-159">**nx_lwm2m_firmware_package_info_set**: *Ange information om uppdaterings paket för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="33f75-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="33f75-160">**nx_lwm2m_firmware_result_set**: *Ange uppdaterings resultat för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="33f75-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="33f75-161">**nx_lwm2m_firmware_state_set**: *Ange uppdaterings tillstånd för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="33f75-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="33f75-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="33f75-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="33f75-163">Skapa LWM2M-klient</span><span class="sxs-lookup"><span data-stu-id="33f75-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-164">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="33f75-165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-165">Description</span></span>

<span data-ttu-id="33f75-166">Den här tjänsten skapar en LWM2M-klient instans som körs i kontexten för en egen ThreadX-tråd.</span><span class="sxs-lookup"><span data-stu-id="33f75-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="33f75-167">LWM2M-klienten implementerar följande OMA LWM2M-objekt: Security (0), Server (1), Access Control (2) och enhet (3).</span><span class="sxs-lookup"><span data-stu-id="33f75-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="33f75-168">Implementeringar av andra objekt måste läggas till av programmet.</span><span class="sxs-lookup"><span data-stu-id="33f75-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-169">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-169">Parameters</span></span>

- <span data-ttu-id="33f75-170">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-171">**ip_ptr**: pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="33f75-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="33f75-172">**packet_pool_ptr**: pekar mot standardpoolen för den här LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="33f75-173">**local_port**: den lokala UDP-port som används för osäker kommunikation.</span><span class="sxs-lookup"><span data-stu-id="33f75-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="33f75-174">**name_ptr**: pekare till LWM2M-klientens slut punkts namn.</span><span class="sxs-lookup"><span data-stu-id="33f75-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="33f75-175">**msisdn_ptr**: pekar på MSISDN där LWM2M-klienten kan nås för användning med SMS-bindningen, kan vara null om SMS-bindning inte stöds.</span><span class="sxs-lookup"><span data-stu-id="33f75-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="33f75-176">**binding_modes**: bindningen och lägena som stöds av LWM2M-klienten måste vara en kombination av flaggor för NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S och NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="33f75-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="33f75-177">**stack_ptr**: pekar på LWM2M för klient tråds tack.</span><span class="sxs-lookup"><span data-stu-id="33f75-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="33f75-178">**stack_size**: LWM2M-klientens tråd storlek.</span><span class="sxs-lookup"><span data-stu-id="33f75-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-179">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-179">Return Values</span></span>

- <span data-ttu-id="33f75-180">**NX_SUCCESS**: LWM2M-klienten har skapats.</span><span class="sxs-lookup"><span data-stu-id="33f75-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="33f75-181">**NX_LWM2M_ERROR**: LWM2M-klienten skapar fel.</span><span class="sxs-lookup"><span data-stu-id="33f75-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="33f75-182">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="33f75-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="33f75-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="33f75-184">Ta bort LWM2M-klient</span><span class="sxs-lookup"><span data-stu-id="33f75-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-185">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-186">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-186">Description</span></span>

<span data-ttu-id="33f75-187">Den här tjänsten tar bort en tidigare skapad LWM2M-klient instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="33f75-188">Alla sessioner som är anslutna till klienten tas också bort av det här anropet.</span><span class="sxs-lookup"><span data-stu-id="33f75-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-189">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-189">Parameters</span></span>

- <span data-ttu-id="33f75-190">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-191">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-191">Return Values</span></span>

- <span data-ttu-id="33f75-192">**NX_SUCCESS**: LWM2M-klienten har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="33f75-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="33f75-193">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="33f75-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="33f75-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="33f75-195">Ange återanrop i enhets objekts program</span><span class="sxs-lookup"><span data-stu-id="33f75-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-196">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="33f75-197">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-197">Description</span></span>

<span data-ttu-id="33f75-198">Den här tjänsten installerar program återanrop för att implementera åtgärder på LWM2M enhets objekt resurser som inte hanteras av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="33f75-199">LWM2M-klienten implementerar följande resurser: felkod (11), Reset-felkod (12) och bindning och lägen som stöds (16). åtgärder för de andra resurserna omdirigeras till programmet.</span><span class="sxs-lookup"><span data-stu-id="33f75-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-200">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-200">Parameters</span></span>

- <span data-ttu-id="33f75-201">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-202">**read_callback**: metoden Read är Read.</span><span class="sxs-lookup"><span data-stu-id="33f75-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="33f75-203">**discover_callback**: återanropet "Discover"-metoden.</span><span class="sxs-lookup"><span data-stu-id="33f75-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="33f75-204">**write_callback**: metoden Write.</span><span class="sxs-lookup"><span data-stu-id="33f75-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="33f75-205">**execute_callback**: "EXECUTE"-metod återanropet.</span><span class="sxs-lookup"><span data-stu-id="33f75-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-206">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-206">Return Values</span></span>

- <span data-ttu-id="33f75-207">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-208">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="33f75-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="33f75-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="33f75-210">Lägg till felkod till enhets objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-211">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="33f75-212">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-212">Description</span></span>

<span data-ttu-id="33f75-213">Den här tjänsten lägger till en ny instans i fel kods resursen (11) för objekt enheten.</span><span class="sxs-lookup"><span data-stu-id="33f75-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-214">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-214">Parameters</span></span>

- <span data-ttu-id="33f75-215">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-216">**kod**: den nya felkoden.</span><span class="sxs-lookup"><span data-stu-id="33f75-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-217">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-217">Return Values</span></span>

- <span data-ttu-id="33f75-218">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-219">**NX_LWM2M_BUFFER_TOO_SMALL**: det maximala antalet lagrade fel koder har nåtts.</span><span class="sxs-lookup"><span data-stu-id="33f75-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="33f75-220">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="33f75-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="33f75-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="33f75-222">Återställa felkoder för enhets objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-223">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-224">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-224">Description</span></span>

<span data-ttu-id="33f75-225">Den här tjänsten tar bort alla fel kods resurs instanser från objektet enhet.</span><span class="sxs-lookup"><span data-stu-id="33f75-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="33f75-226">Det motsvarar att köra fel koden för resurs återställning (12).</span><span class="sxs-lookup"><span data-stu-id="33f75-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-227">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-227">Parameters</span></span>

- <span data-ttu-id="33f75-228">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-229">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-229">Return Values</span></span>

- <span data-ttu-id="33f75-230">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-231">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="33f75-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="33f75-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="33f75-233">Signal ändring för enhets objekt resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-234">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="33f75-235">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-235">Description</span></span>

<span data-ttu-id="33f75-236">Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs av objekt enheten har ändrats.</span><span class="sxs-lookup"><span data-stu-id="33f75-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="33f75-237">LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-238">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-238">Parameters</span></span>

- <span data-ttu-id="33f75-239">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-240">**resurs**: pekar till strukturen som beskriver den resurs som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="33f75-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-241">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-241">Return Values</span></span>

- <span data-ttu-id="33f75-242">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-243">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="33f75-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="33f75-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="33f75-245">Lås LWM2M-klient</span><span class="sxs-lookup"><span data-stu-id="33f75-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-246">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-247">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-247">Description</span></span>

<span data-ttu-id="33f75-248">Den här tjänsten låser LWM2M-klienten för att förhindra concurent-åtkomst till LWM2M-objekt från servrar eller någon annan program tråd.</span><span class="sxs-lookup"><span data-stu-id="33f75-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="33f75-249">Om LWM2M-klienten är låst av en annan tråd, kommer funktionen att blockeras tills LWM2M-klienten har låsts upp.</span><span class="sxs-lookup"><span data-stu-id="33f75-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="33f75-250">Anrop till nx_lwm2m_client_lock ()/nx_lwm2m_client_unlock ()-par kan kapslas.</span><span class="sxs-lookup"><span data-stu-id="33f75-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-251">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-251">Parameters</span></span>

- <span data-ttu-id="33f75-252">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-253">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-253">Return Values</span></span>

- <span data-ttu-id="33f75-254">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-255">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="33f75-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="33f75-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="33f75-257">Lägga till objekt implementering i LWM2M-klienten</span><span class="sxs-lookup"><span data-stu-id="33f75-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-258">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-259">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-259">Description</span></span>

<span data-ttu-id="33f75-260">Den här tjänsten lägger till en ny objekt implementering i LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-261">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-261">Parameters</span></span>

- <span data-ttu-id="33f75-262">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-263">**object_ptr**: pekar mot strukturen som definierar objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="33f75-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-264">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-264">Return Values</span></span>

- <span data-ttu-id="33f75-265">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-266">**NX_LWM2M_ALREADY_EXIST**: objekt-ID: t finns redan.</span><span class="sxs-lookup"><span data-stu-id="33f75-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="33f75-267">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="33f75-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="33f75-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="33f75-269">Skapa en ny objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-270">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-271">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-271">Description</span></span>

<span data-ttu-id="33f75-272">Den här tjänsten utför en "skapa"-åtgärd på ett objekt av LWM2M-klienten för att skapa en ny objekt instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-273">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-273">Parameters</span></span>

- <span data-ttu-id="33f75-274">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-275">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-276">**instance_id_ptr**: pekaren till ID: t för den nya instansen kan vara null om LWM2M-klienten måste tilldela ett instans-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="33f75-277">Om ID: t är det reserverade värdet 65535, tilldelar LWM2M-klienten ett instans-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="33f75-278">Om det tilldelade ID: t inte är NULL returneras det efter anropet.</span><span class="sxs-lookup"><span data-stu-id="33f75-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="33f75-279">**num_values**: antalet värden som ska anges.</span><span class="sxs-lookup"><span data-stu-id="33f75-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="33f75-280">**values_ptr**: pekar mot en matris med resurs värden för att initiera den nya objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="33f75-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-281">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-281">Return Values</span></span>

- <span data-ttu-id="33f75-282">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-283">**NX_LWM2M_ALREADY_EXIST**: ID: t för objekt instansen finns redan.</span><span class="sxs-lookup"><span data-stu-id="33f75-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="33f75-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: objektet har inte stöd för att skapa en instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="33f75-285">**NX_LWM2M_NO_MEMORY**: det går inte att allokera minne för att lagra den nya instansen.</span><span class="sxs-lookup"><span data-stu-id="33f75-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="33f75-286">**NX_LWM2M_NOT_FOUND**: objekt-ID: t finns inte.</span><span class="sxs-lookup"><span data-stu-id="33f75-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="33f75-287">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="33f75-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="33f75-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="33f75-289">Ta bort en objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-290">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="33f75-291">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-291">Description</span></span>

<span data-ttu-id="33f75-292">Den här tjänsten utför en borttagnings åtgärd på en objekt instans av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-293">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-293">Parameters</span></span>

- <span data-ttu-id="33f75-294">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-295">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-296">**instance_id**: ID för objekt instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-297">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-297">Return Values</span></span>

- <span data-ttu-id="33f75-298">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: objektet har inte stöd för borttagning av instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="33f75-300">**NX_LWM2M_NOT_FOUND**: ID för objekt-ID eller objekt instans saknas.</span><span class="sxs-lookup"><span data-stu-id="33f75-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="33f75-301">NX_PTR_ERROR ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="33f75-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="33f75-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="33f75-303">Identifiera resurser för en objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-304">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-305">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-305">Description</span></span>

<span data-ttu-id="33f75-306">Den här tjänsten utför en "Discover"-åtgärd på en objekt instans av LWM2M-klienten, vilket returnerar listan över resurser som implementeras av objektet.</span><span class="sxs-lookup"><span data-stu-id="33f75-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-307">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-307">Parameters</span></span>

- <span data-ttu-id="33f75-308">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-309">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-310">**instance_id**: ID för objekt instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="33f75-311">**num_resources_ptr**: om du vill ange storleken på måldomänkontrollanten vid utdata anger du antalet element som skrivs till bufferten.</span><span class="sxs-lookup"><span data-stu-id="33f75-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="33f75-312">**resources_ptr**: pekar mot målcachen.</span><span class="sxs-lookup"><span data-stu-id="33f75-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-313">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-313">Return Values</span></span>

- <span data-ttu-id="33f75-314">**NX_SUCCESS**: åtgärden lyckades..</span><span class="sxs-lookup"><span data-stu-id="33f75-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="33f75-315">**NX_LWM2M_BUFFER_TOO_SMALL**: bufferten är för liten för att lagra listan över resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="33f75-316">**NX_LWM2M_NOT_FOUND**: ID för objekt-ID eller objekt instans saknas.</span><span class="sxs-lookup"><span data-stu-id="33f75-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="33f75-317">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="33f75-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="33f75-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="33f75-319">Kör resurs för en objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-320">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="33f75-321">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-321">Description</span></span>

<span data-ttu-id="33f75-322">Den här tjänsten utför åtgärden kör på en objekt instans resurs för LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-323">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-323">Parameters</span></span>

- <span data-ttu-id="33f75-324">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-325">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-326">**instance_id**: ID för objekt instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="33f75-327">**resource_id**: resurs-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="33f75-328">**arguments_ptr**: pekar mot argumenten för körnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="33f75-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="33f75-329">Kan vara NULL om arguments_length är noll.</span><span class="sxs-lookup"><span data-stu-id="33f75-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="33f75-330">**arguments_length**: argumentens längd.</span><span class="sxs-lookup"><span data-stu-id="33f75-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-331">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-331">Return Values</span></span>

- <span data-ttu-id="33f75-332">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: resursen har inte stöd för körnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="33f75-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="33f75-334">**NX_LWM2M_NOT_FOUND**: objekt-ID, objekt instans-ID eller resurs-ID finns inte.</span><span class="sxs-lookup"><span data-stu-id="33f75-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="33f75-335">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="33f75-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="33f75-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="33f75-337">Hämta listan över objekt som implementeras av LWM2M-klienten</span><span class="sxs-lookup"><span data-stu-id="33f75-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-338">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-339">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-339">Description</span></span>

<span data-ttu-id="33f75-340">Den här tjänsten returnerar ID: t för nästa objekt som implementeras av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="33f75-341">Om aktuellt objekt-ID är inställt på NX_LWM2M_RESERVED_ID (65535) returneras det första objekt-ID: t.</span><span class="sxs-lookup"><span data-stu-id="33f75-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-342">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-342">Parameters</span></span>

- <span data-ttu-id="33f75-343">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-344">**object_id_ptr**: pekar mot aktuellt objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="33f75-345">Vid retur innehåller nästa objekt-ID som implementeras av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-346">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-346">Return Values</span></span>

- <span data-ttu-id="33f75-347">**NX_SUCCESS**: åtgärden lyckades..</span><span class="sxs-lookup"><span data-stu-id="33f75-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="33f75-348">**NX_LWM2M_NOT_FOUND**: angivet objekt-ID är det sista i databasen.</span><span class="sxs-lookup"><span data-stu-id="33f75-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="33f75-349">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="33f75-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="33f75-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="33f75-351">Hämta listan över instanser av ett objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-352">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-353">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-353">Description</span></span>

<span data-ttu-id="33f75-354">Den här tjänsten returnerar ID: t för nästa objekt instans av det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="33f75-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="33f75-355">Om det aktuella instans-ID: t är inställt på NX_LWM2M_RESERVED_ID (65535) returneras ID: t för den första instansen.</span><span class="sxs-lookup"><span data-stu-id="33f75-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-356">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-356">Parameters</span></span>

- <span data-ttu-id="33f75-357">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-358">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-359">**instance_id_ptr**: pekar mot aktuellt objekt instans-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="33f75-360">Vid retur innehåller nästa instans-ID för objektet.</span><span class="sxs-lookup"><span data-stu-id="33f75-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-361">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-361">Return Values</span></span>

- <span data-ttu-id="33f75-362">**NX_SUCCESS**: åtgärden lyckades..</span><span class="sxs-lookup"><span data-stu-id="33f75-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="33f75-363">**NX_LWM2M_NOT_FOUND**: det aktuella instans-ID: t är det sista objektet eller objekt-ID: t är inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="33f75-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="33f75-364">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="33f75-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="33f75-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="33f75-366">Läsa resurs värden för en objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-367">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="33f75-368">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-368">Description</span></span>

<span data-ttu-id="33f75-369">Den här tjänsten utför en Läs åtgärd på en objekt instans av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-370">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-370">Parameters</span></span>

- <span data-ttu-id="33f75-371">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-372">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-373">**instance_id**: ID för objekt instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="33f75-374">**num_values**: antalet resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="33f75-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="33f75-375">**values_ptr**: pekar mot en matris med NX_LWM2M_RESOURCE som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="33f75-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="33f75-376">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="33f75-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-377">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-377">Return Values</span></span>

- <span data-ttu-id="33f75-378">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: en resurs har inte stöd för Läs åtgärden.</span><span class="sxs-lookup"><span data-stu-id="33f75-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="33f75-380">**NX_LWM2M_NOT_FOUND**: objekt-ID, objekt instans-ID eller resurs-ID finns inte.</span><span class="sxs-lookup"><span data-stu-id="33f75-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="33f75-381">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="33f75-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="33f75-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="33f75-383">Ändra resurs värden för en objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-384">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="33f75-385">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-385">Description</span></span>

<span data-ttu-id="33f75-386">Den här tjänsten utför en Skriv åtgärd på en objekt instans av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="33f75-387">Följande Skriv åtgärder kan anges för parametern *write_op* :</span><span class="sxs-lookup"><span data-stu-id="33f75-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="33f75-388">**0** &mdash; del uppdatering: lägger till eller uppdaterar resurser som finns i det nya värdet och låter andra befintliga resurser ändras,</span><span class="sxs-lookup"><span data-stu-id="33f75-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="33f75-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Ersätt instans: ersätter objekt instansen med de nya angivna resurs värdena.</span><span class="sxs-lookup"><span data-stu-id="33f75-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="33f75-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Ersätt resurs: ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser).</span><span class="sxs-lookup"><span data-stu-id="33f75-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="33f75-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap-skrivning: indikerar ett anrop från en bootstrap-sekvens.</span><span class="sxs-lookup"><span data-stu-id="33f75-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-392">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-392">Parameters</span></span>

- <span data-ttu-id="33f75-393">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-394">**object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="33f75-395">**instance_id**: ID för objekt instans.</span><span class="sxs-lookup"><span data-stu-id="33f75-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="33f75-396">**num_values**: antalet resurser som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="33f75-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="33f75-397">**values_ptr**: pekar mot en matris med NX_LWM2M_RESOURCE som innehåller ID: n för resurserna, typerna och värdena som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="33f75-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="33f75-398">**write_op**: typ av Skriv åtgärd.</span><span class="sxs-lookup"><span data-stu-id="33f75-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-399">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-399">Return Values</span></span>

- <span data-ttu-id="33f75-400">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-401">**NX_LWM2M_BAD_ENCODING**: resurs typen är inte giltig.</span><span class="sxs-lookup"><span data-stu-id="33f75-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="33f75-402">**NX_LWM2M_BUFFER_TOO_SMALL**: längden på ett värde är för stor för att lagras i instansen.</span><span class="sxs-lookup"><span data-stu-id="33f75-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="33f75-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: en resurs har inte stöd för Skriv åtgärden.</span><span class="sxs-lookup"><span data-stu-id="33f75-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="33f75-404">**NX_LWM2M_NO_MEMORY**: det går inte att allokera minne för att lagra ett resurs värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="33f75-405">**NX_LWM2M_NOT_ACCEPTABLE**: värdet för en resurs är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="33f75-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="33f75-406">**NX_LWM2M_NOT_FOUND**: objekt-ID, objekt instans-ID eller resurs-ID finns inte.</span><span class="sxs-lookup"><span data-stu-id="33f75-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="33f75-407">NX_OPTION_ERROR: ogiltig typ av Skriv åtgärd.</span><span class="sxs-lookup"><span data-stu-id="33f75-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="33f75-408">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="33f75-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="33f75-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="33f75-410">Ange återanrop för hantering av säkerhets objekt</span><span class="sxs-lookup"><span data-stu-id="33f75-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-411">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="33f75-412">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-412">Description</span></span>

<span data-ttu-id="33f75-413">Den här tjänsten installerar återanrop för program för att implementera åtgärder på LWM2M säkerhets objekt resurser som är relaterade till säkerhets nycklarna.</span><span class="sxs-lookup"><span data-stu-id="33f75-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="33f75-414">LWM2M-klienten delegerar hantering av säkerhets nycklar till programmet under bootstrap-sessionerna, och återanropen anropas när bootstrap-servern skriver eller tar bort följande resurser på en säkerhets objekts instans: offentlig nyckel eller identitet (3), serverns offentliga nyckel (4), hemlig nyckel (5).</span><span class="sxs-lookup"><span data-stu-id="33f75-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="33f75-415">Programmet ansvarar för att lagra nycklarnas data och för att konfigurera de DTLS-sessioner som används av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-416">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-416">Parameters</span></span>

- <span data-ttu-id="33f75-417">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="33f75-418">**write_callback**: det går inte att anropa Key-metoden Write.</span><span class="sxs-lookup"><span data-stu-id="33f75-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="33f75-419">**delete_callback**: den "ta bort" nyckel metoden motringning.</span><span class="sxs-lookup"><span data-stu-id="33f75-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-420">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-420">Return Values</span></span>

- <span data-ttu-id="33f75-421">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-422">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="33f75-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="33f75-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="33f75-424">Starta en-session med en Start Server</span><span class="sxs-lookup"><span data-stu-id="33f75-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-425">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="33f75-426">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-426">Description</span></span>

<span data-ttu-id="33f75-427">Den här tjänsten startar en session med en Start Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="33f75-428">Servern måste ha en motsvarande säkerhets instans i objektet Security.</span><span class="sxs-lookup"><span data-stu-id="33f75-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="33f75-429">Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.</span><span class="sxs-lookup"><span data-stu-id="33f75-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="33f75-430">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-431">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-431">Parameters</span></span>

- <span data-ttu-id="33f75-432">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="33f75-433">**security_id**: Start serverns säkerhets instans-ID måste vara inställt på NX_LWM2M_RESERVED_ID (65535) om ingen säkerhets instans har definierats för bootstrap-servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="33f75-434">**ip_address**: SERVERns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="33f75-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="33f75-435">**port**: SERVERns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="33f75-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-436">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-436">Return Values</span></span>

- <span data-ttu-id="33f75-437">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-438">**NX_LWM2M_NOT_FOUND**: det finns ingen säkerhets objekt instans som motsvarar säkerhets instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="33f75-439">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="33f75-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="33f75-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="33f75-441">Starta en säker session med en Start Server</span><span class="sxs-lookup"><span data-stu-id="33f75-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-442">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="33f75-443">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-443">Description</span></span>

<span data-ttu-id="33f75-444">Den här tjänsten startar en session med en Start Server med en säker DTLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="33f75-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="33f75-445">Servern måste ha en motsvarande säkerhets instans i objektet Security.</span><span class="sxs-lookup"><span data-stu-id="33f75-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="33f75-446">DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="33f75-447">NX_SECURE_ENABLE_DTLS måste definieras.</span><span class="sxs-lookup"><span data-stu-id="33f75-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="33f75-448">Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.</span><span class="sxs-lookup"><span data-stu-id="33f75-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="33f75-449">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-450">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-450">Parameters</span></span>

- <span data-ttu-id="33f75-451">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="33f75-452">**security_id**: Start serverns säkerhets instans-ID måste vara inställt på NX_LWM2M_RESERVED_ID (65535) om ingen säkerhets instans har definierats för bootstrap-servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="33f75-453">**ip_address**: SERVERns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="33f75-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="33f75-454">**port**: SERVERns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="33f75-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="33f75-455">**dtls_session_ptr**: DTLS-sessionen som ska användas för bootstrap-sessionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="33f75-456">**dtls_local_port**: den lokala UDP-port som används för DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-457">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-457">Return Values</span></span>

- <span data-ttu-id="33f75-458">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-459">**NX_LWM2M_NOT_FOUND**: det finns ingen säkerhets objekt instans som motsvarar säkerhets instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="33f75-460">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="33f75-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="33f75-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="33f75-462">Skapa LWM2M-klientsession</span><span class="sxs-lookup"><span data-stu-id="33f75-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-463">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="33f75-464">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-464">Description</span></span>

<span data-ttu-id="33f75-465">Den här tjänsten skapar en ny LWM2M-klientsession som är ansluten till en befintlig LWM2M-klient.</span><span class="sxs-lookup"><span data-stu-id="33f75-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="33f75-466">Sessionen används av LWM2M-klienten för att kommunicera med en Start Server eller en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="33f75-467">Programmet måste tillhandahålla en callback-funktion som anropas när sessionens tillstånd uppdateras.</span><span class="sxs-lookup"><span data-stu-id="33f75-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-468">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-468">Parameters</span></span>

- <span data-ttu-id="33f75-469">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="33f75-470">**client_ptr**: pekar mot den tidigare skapade LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="33f75-471">**state_callback**: motringning till program som anropas när sessionens tillstånd har ändrats.</span><span class="sxs-lookup"><span data-stu-id="33f75-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-472">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-472">Return Values</span></span>

- <span data-ttu-id="33f75-473">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-474">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="33f75-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="33f75-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="33f75-476">Ta bort LWM2M-klientsession</span><span class="sxs-lookup"><span data-stu-id="33f75-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-477">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-478">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-478">Description</span></span>

<span data-ttu-id="33f75-479">Den här tjänsten tar bort en LWM2M-klientsession.</span><span class="sxs-lookup"><span data-stu-id="33f75-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="33f75-480">När en LWM2M-klient tas bort genom att anropa nx_lwm2m_client_delete alla sessioner som är anslutna till klienten också bort.</span><span class="sxs-lookup"><span data-stu-id="33f75-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-481">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-481">Parameters</span></span>

- <span data-ttu-id="33f75-482">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-483">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-483">Return Values</span></span>

- <span data-ttu-id="33f75-484">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-485">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="33f75-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="33f75-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="33f75-487">Avsluta en session med en LWM2M-Server</span><span class="sxs-lookup"><span data-stu-id="33f75-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-488">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-489">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-489">Description</span></span>

<span data-ttu-id="33f75-490">Den här tjänsten utför en "avregistrera"-åtgärd på en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-491">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-491">Parameters</span></span>

- <span data-ttu-id="33f75-492">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-493">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-493">Return Values</span></span>

- <span data-ttu-id="33f75-494">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-495">**NX_LWM2M_NOT_REGISTERED**: klienten är inte registrerad på servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="33f75-496">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="33f75-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="33f75-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="33f75-498">Hämta senaste fel i en session</span><span class="sxs-lookup"><span data-stu-id="33f75-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-499">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-500">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-500">Description</span></span>

<span data-ttu-id="33f75-501">Den här tjänsten returnerar felkoden för sessionen när sessionen är i ett fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="33f75-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-502">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-502">Parameters</span></span>

- <span data-ttu-id="33f75-503">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-504">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-504">Return Values</span></span>

- <span data-ttu-id="33f75-505">**NX_SUCCESS**: sessionen har fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="33f75-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="33f75-506">**NX_LWM2M_ADDRESS_ERROR**: ogiltig server adress.</span><span class="sxs-lookup"><span data-stu-id="33f75-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="33f75-507">**NX_LWM2M_BUFFER_TOO_SMALL**: nytto lasten för begäran får inte plats i nätverksmappen.</span><span class="sxs-lookup"><span data-stu-id="33f75-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="33f75-508">**NX_LWM2M_DTLS_ERROR**: det gick inte att upprätta en säker anslutning till servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="33f75-509">**NX_LWM2M_ERROR**: okänt fel.</span><span class="sxs-lookup"><span data-stu-id="33f75-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="33f75-510">**NX_LWM2M_FORBIDDEN**: registreringen nekades av servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="33f75-511">**NX_LWM2M_NOT_FOUND**: klienten hittades inte av servern vid uppdatering/avregistrering.</span><span class="sxs-lookup"><span data-stu-id="33f75-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="33f75-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: den server objekt instans som motsvarar sessionen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="33f75-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="33f75-513">**NX_LWM2M_TIMED_OUT**: inget svar från servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="33f75-514">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="33f75-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="33f75-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="33f75-516">Starta en-session med en LWM2M-Server</span><span class="sxs-lookup"><span data-stu-id="33f75-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-517">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="33f75-518">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-518">Description</span></span>

<span data-ttu-id="33f75-519">Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="33f75-520">Servern måste ha en motsvarande Server instans i objektet Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="33f75-521">Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.</span><span class="sxs-lookup"><span data-stu-id="33f75-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="33f75-522">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.</span><span class="sxs-lookup"><span data-stu-id="33f75-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-523">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-523">Parameters</span></span>

- <span data-ttu-id="33f75-524">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="33f75-525">**server_id**: LWM2M-serverns korta Server-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="33f75-526">**ip_address**: SERVERns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="33f75-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="33f75-527">**port**: SERVERns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="33f75-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-528">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-528">Return Values</span></span>

- <span data-ttu-id="33f75-529">**NX_SUCCESS**: åtgärden lyckades..</span><span class="sxs-lookup"><span data-stu-id="33f75-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="33f75-530">**NX_LWM2M_NOT_FOUND**: det finns ingen Server objekt instans som motsvarar det korta Server-ID: t.</span><span class="sxs-lookup"><span data-stu-id="33f75-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="33f75-531">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="33f75-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="33f75-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="33f75-533">Starta en säker session med en LWM2M-Server</span><span class="sxs-lookup"><span data-stu-id="33f75-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-534">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="33f75-535">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-535">Description</span></span>

<span data-ttu-id="33f75-536">Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-server med en säker DTLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="33f75-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="33f75-537">Servern måste ha en motsvarande Server instans i objektet Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="33f75-538">DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="33f75-539">NX_SECURE_ENABLE_DTLS måste definieras.</span><span class="sxs-lookup"><span data-stu-id="33f75-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="33f75-540">Varje DTLS-session använder sin egen UDP-socket för kommunikation, så den lokala port dtls_local_port måste vara olika för varje session om programmet skapar flera säkra sessioner.</span><span class="sxs-lookup"><span data-stu-id="33f75-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="33f75-541">Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.</span><span class="sxs-lookup"><span data-stu-id="33f75-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="33f75-542">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.</span><span class="sxs-lookup"><span data-stu-id="33f75-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-543">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-543">Parameters</span></span>

- <span data-ttu-id="33f75-544">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="33f75-545">**server_id**: LWM2M-serverns korta Server-ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="33f75-546">**ip_address**: SERVERns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="33f75-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="33f75-547">**port**: SERVERns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="33f75-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="33f75-548">**dtls_session_ptr**: DTLS-sessionen som ska användas för LWM2M-sessionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="33f75-549">**dtls_local_port**: den lokala UDP-port som används för DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-550">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-550">Return Values</span></span>

- <span data-ttu-id="33f75-551">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-552">**NX_LWM2M_NOT_FOUND**: det finns ingen Server objekt instans som motsvarar det korta Server-ID: t.</span><span class="sxs-lookup"><span data-stu-id="33f75-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="33f75-553">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="33f75-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="33f75-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="33f75-555">Uppdatera en session med en LWM2M-Server</span><span class="sxs-lookup"><span data-stu-id="33f75-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-556">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-557">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-557">Description</span></span>

<span data-ttu-id="33f75-558">Den här tjänsten utför en uppdaterings åtgärd på en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-559">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-559">Parameters</span></span>

- <span data-ttu-id="33f75-560">**session_ptr**: pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="33f75-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-561">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-561">Return Values</span></span>

- <span data-ttu-id="33f75-562">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-563">**NX_LWM2M_NOT_REGISTERED**: klienten är inte registrerad på servern.</span><span class="sxs-lookup"><span data-stu-id="33f75-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="33f75-564">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="33f75-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="33f75-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="33f75-566">Lås upp LWM2M-klienten</span><span class="sxs-lookup"><span data-stu-id="33f75-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-567">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-568">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-568">Description</span></span>

<span data-ttu-id="33f75-569">Den här tjänsten låser upp LWM2M-previoulsy som låsts av ett anrop till nx_lwm2m_client_unlock ().</span><span class="sxs-lookup"><span data-stu-id="33f75-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-570">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-570">Parameters</span></span>

- <span data-ttu-id="33f75-571">**client_ptr**: pekar mot LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="33f75-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-572">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-572">Return Values</span></span>

- <span data-ttu-id="33f75-573">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-574">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="33f75-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="33f75-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="33f75-576">Skapa uppdaterings objekt för inbyggd program vara</span><span class="sxs-lookup"><span data-stu-id="33f75-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-577">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="33f75-578">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-578">Description</span></span>

<span data-ttu-id="33f75-579">Den här tjänsten initierar ett uppdaterings objekt för inbyggd program vara och lägger till objektet i en tidigare skapad LWM2M-klient.</span><span class="sxs-lookup"><span data-stu-id="33f75-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="33f75-580">Objektet uppdatering av inbyggd program vara implementerar resurserna för kommunikation med en LWM2M-Server, men programmet måste tillhandahålla återanrop för att implementera de faktiska åtgärderna i den inbyggda program varan (dowloading, lagring och uppdatering av den inbyggda program varan).</span><span class="sxs-lookup"><span data-stu-id="33f75-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="33f75-581">Parametern Protocols anger vilka protokoll som stöds av programmet för att hämta den inbyggda program varan med "Package URI"-resursen, följande flaggor definieras:</span><span class="sxs-lookup"><span data-stu-id="33f75-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="33f75-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span><span class="sxs-lookup"><span data-stu-id="33f75-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-583">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-583">Parameters</span></span>

- <span data-ttu-id="33f75-584">**firmware_ptr**: pekar mot objekt kontroll blocket för inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="33f75-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="33f75-585">**client_ptr**: pekare till PREVISOUSLY skapade LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="33f75-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="33f75-586">**protokoll**: flaggor som anger vilka protokoll som stöds av PAKETets URI-resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="33f75-587">**package_callback**: måste vara null [TBD].</span><span class="sxs-lookup"><span data-stu-id="33f75-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="33f75-588">**package_uri_callback**: motringning används för att implementera PAKETets URI-resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="33f75-589">**update_callback**: motringning används för att implementera uppdaterings resursen.</span><span class="sxs-lookup"><span data-stu-id="33f75-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-590">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-590">Return Values</span></span>

- <span data-ttu-id="33f75-591">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-592">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="33f75-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="33f75-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="33f75-594">Ange information om uppdaterings paket för inbyggd program vara</span><span class="sxs-lookup"><span data-stu-id="33f75-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-595">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="33f75-596">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-596">Description</span></span>

<span data-ttu-id="33f75-597">Den här tjänsten ändrar värdena för "PkgName" (6) och "PkgVersion" (7) resurser i uppdaterings objekt för inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="33f75-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-598">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-598">Parameters</span></span>

- <span data-ttu-id="33f75-599">**firmware_ptr**: pekar mot uppdaterings objekt för inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="33f75-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="33f75-600">**namn**: det nya värdet för paket namnet.</span><span class="sxs-lookup"><span data-stu-id="33f75-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="33f75-601">**version**: det nya värdet för paket versionen.</span><span class="sxs-lookup"><span data-stu-id="33f75-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-602">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-602">Return Values</span></span>

- <span data-ttu-id="33f75-603">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-604">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="33f75-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="33f75-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="33f75-606">Ange uppdaterings resultat för inbyggd program vara</span><span class="sxs-lookup"><span data-stu-id="33f75-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-607">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="33f75-608">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-608">Description</span></span>

<span data-ttu-id="33f75-609">Den här tjänsten ändrar värdet för resursen uppdaterings resultat (5) för objektet för den inbyggda program varan.</span><span class="sxs-lookup"><span data-stu-id="33f75-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-610">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-610">Parameters</span></span>

- <span data-ttu-id="33f75-611">**firmware_ptr**: pekar mot uppdaterings objekt för inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="33f75-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="33f75-612">**resultat**: det nya värdet för resursen uppdaterings resultat.</span><span class="sxs-lookup"><span data-stu-id="33f75-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-613">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-613">Return Values</span></span>

- <span data-ttu-id="33f75-614">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-615">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="33f75-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="33f75-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="33f75-617">Ange uppdaterings tillstånd för inbyggd program vara</span><span class="sxs-lookup"><span data-stu-id="33f75-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-618">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="33f75-619">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-619">Description</span></span>

<span data-ttu-id="33f75-620">Den här tjänsten ändrar värdet för "State"-resursen (3) för objektet med uppdatering av inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="33f75-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-621">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-621">Parameters</span></span>

- <span data-ttu-id="33f75-622">**firmware_ptr**: pekar mot uppdaterings objekt för inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="33f75-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="33f75-623">**status**: det nya värdet för tillstånds resursen.</span><span class="sxs-lookup"><span data-stu-id="33f75-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-624">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-624">Return Values</span></span>

- <span data-ttu-id="33f75-625">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-626">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="33f75-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="33f75-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="33f75-628">Signal ändring för ett resurs värde för en objekt instans</span><span class="sxs-lookup"><span data-stu-id="33f75-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-629">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="33f75-630">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-630">Description</span></span>

<span data-ttu-id="33f75-631">Den här tjänsten används av en objekt implementering för att signalera LWM2M-klienten om att ett av resursens värde har ändrats.</span><span class="sxs-lookup"><span data-stu-id="33f75-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="33f75-632">LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="33f75-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-633">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-633">Parameters</span></span>

- <span data-ttu-id="33f75-634">**object_ptr**: pekar mot objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="33f75-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="33f75-635">**instance_ptr**: pekar mot objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="33f75-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="33f75-636">**resurs**: pekar till strukturen som beskriver den resurs som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="33f75-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-637">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-637">Return Values</span></span>

- <span data-ttu-id="33f75-638">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-639">NX_PTR_ERROR: ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="33f75-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="33f75-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="33f75-641">Hämta värdet för en boolesk resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-642">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-643">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-643">Description</span></span>

<span data-ttu-id="33f75-644">Tjänsten hämtar värdet för en boolesk resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-645">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-645">Parameters</span></span>

- <span data-ttu-id="33f75-646">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-647">**bool_ptr**: pekar mot målets booleska värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-648">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-648">Return Values</span></span>

- <span data-ttu-id="33f75-649">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-650">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="33f75-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="33f75-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="33f75-652">Hämta värdet för en 32-bitars svävande punkt resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-654">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-654">Description</span></span>

<span data-ttu-id="33f75-655">Tjänsten hämtar värdet för en 32-bitars svävande punkt resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-656">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-656">Parameters</span></span>

- <span data-ttu-id="33f75-657">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-658">**float32_ptr**: pekar på målets 32-bitars flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-659">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-659">Return Values</span></span>

- <span data-ttu-id="33f75-660">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-661">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="33f75-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="33f75-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="33f75-663">Hämta värdet för en 64-bitars svävande punkt resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-664">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-665">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-665">Description</span></span>

<span data-ttu-id="33f75-666">Tjänsten hämtar värdet för en 64-bitars svävande punkt resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-667">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-667">Parameters</span></span>

- <span data-ttu-id="33f75-668">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-669">**float64_ptr**: pekar på målets 64-bitars flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-670">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-670">Return Values</span></span>

- <span data-ttu-id="33f75-671">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-672">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="33f75-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="33f75-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="33f75-674">Hämta värdet för en 32-bitars heltals resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-675">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-676">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-676">Description</span></span>

<span data-ttu-id="33f75-677">Tjänsten hämtar värdet för en 32-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-678">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-678">Parameters</span></span>

- <span data-ttu-id="33f75-679">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-680">**int32_ptr**: pekar mot målet 32-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-681">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-681">Return Values</span></span>

- <span data-ttu-id="33f75-682">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-683">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett heltals värde, eller så ryms inte heltalet i ett 32-bitars tal.</span><span class="sxs-lookup"><span data-stu-id="33f75-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="33f75-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="33f75-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="33f75-685">Hämta värdet för en 64-bitars heltals resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-686">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-687">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-687">Description</span></span>

<span data-ttu-id="33f75-688">Tjänsten hämtar värdet för en 64-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-689">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-689">Parameters</span></span>

- <span data-ttu-id="33f75-690">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-691">**int64_ptr**: pekar mot målet 64-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-692">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-692">Return Values</span></span>

- <span data-ttu-id="33f75-693">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-694">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett heltals värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="33f75-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="33f75-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="33f75-696">Hämta värdet för en objekt länk resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-697">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-698">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-698">Description</span></span>

<span data-ttu-id="33f75-699">Tjänsten hämtar värdet för en objekt länk resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-700">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-700">Parameters</span></span>

- <span data-ttu-id="33f75-701">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-702">**objlnk_ptr**: pekar mot länk värde för mål objekt.</span><span class="sxs-lookup"><span data-stu-id="33f75-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-703">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-703">Return Values</span></span>

- <span data-ttu-id="33f75-704">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-705">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett objekt länk värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="33f75-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="33f75-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="33f75-707">Hämta värdet för en ogenomskinlig resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-708">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-709">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-709">Description</span></span>

<span data-ttu-id="33f75-710">Tjänsten hämtar värdet för en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="33f75-711">Ett ogenomskinligt resurs värde består av en pekare till en buffert och en längd.</span><span class="sxs-lookup"><span data-stu-id="33f75-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-712">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-712">Parameters</span></span>

- <span data-ttu-id="33f75-713">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-714">**opaque_ptr_ptr**: pekar mot målets täckande buffer-pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="33f75-715">**opaque_length_ptr**: pekar mot målets täckande buffertlängd.</span><span class="sxs-lookup"><span data-stu-id="33f75-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-716">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-716">Return Values</span></span>

- <span data-ttu-id="33f75-717">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-718">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett ogenomskinligt värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="33f75-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="33f75-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="33f75-720">Hämta värdet för en sträng resurs</span><span class="sxs-lookup"><span data-stu-id="33f75-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-721">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-722">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-722">Description</span></span>

<span data-ttu-id="33f75-723">Tjänsten hämtar värdet för en sträng resurs.</span><span class="sxs-lookup"><span data-stu-id="33f75-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-724">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-724">Parameters</span></span>

- <span data-ttu-id="33f75-725">**värde**: pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="33f75-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="33f75-726">**string_ptr_ptr**: pekar mot mål sträng pekaren.</span><span class="sxs-lookup"><span data-stu-id="33f75-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="33f75-727">**string_length_ptr**: pekar mot mål strängens längd.</span><span class="sxs-lookup"><span data-stu-id="33f75-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="33f75-728">Kan vara NULL om strängen är null-terminerad.</span><span class="sxs-lookup"><span data-stu-id="33f75-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-729">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-729">Return Values</span></span>

- <span data-ttu-id="33f75-730">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-731">**NX_LWM2M_BAD_ENCODING**: resursens värde är inte ett sträng värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="33f75-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="33f75-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="33f75-733">Hämta värdet för en boolesk resurs flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-734">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-735">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-735">Description</span></span>

<span data-ttu-id="33f75-736">Tjänsten hämtar värdet för en boolesk resurs instans från flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-737">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-737">Parameters</span></span>

- <span data-ttu-id="33f75-738">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-739">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-740">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-741">**bool_ptr**: pekar mot målets booleska värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-742">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-742">Return Values</span></span>

- <span data-ttu-id="33f75-743">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-744">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-745">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="33f75-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="33f75-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="33f75-747">Hämta värdet för en 32-bitars flytt ALS plats med flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-748">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-749">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-749">Description</span></span>

<span data-ttu-id="33f75-750">Tjänsten hämtar värdet för en 32-bitars flytt ALS resurs instans från flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-751">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-751">Parameters</span></span>

- <span data-ttu-id="33f75-752">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-753">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-754">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-755">**float32_ptr**: pekar på målets 32-bitars flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-756">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-756">Return Values</span></span>

- <span data-ttu-id="33f75-757">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-758">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-759">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="33f75-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="33f75-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="33f75-761">Hämta värdet för en 64-bitars flytt ALS plats med flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-762">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-763">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-763">Description</span></span>

<span data-ttu-id="33f75-764">Tjänsten hämtar värdet för en 64-bitars flytt ALS resurs instans från flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-765">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-765">Parameters</span></span>

- <span data-ttu-id="33f75-766">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-767">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-768">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-769">**float64_ptr**: pekar på målets 64-bitars flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-770">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-770">Return Values</span></span>

- <span data-ttu-id="33f75-771">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-772">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-773">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="33f75-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="33f75-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="33f75-775">Hämta värdet för ett 32-bitars heltal flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-776">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-777">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-777">Description</span></span>

<span data-ttu-id="33f75-778">Tjänsten hämtar värdet för en 32-bitars heltals resurs instans från en flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-779">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-779">Parameters</span></span>

- <span data-ttu-id="33f75-780">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-781">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-782">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-783">**int32_ptr**: pekar mot målet 32-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-784">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-784">Return Values</span></span>

- <span data-ttu-id="33f75-785">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-786">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-787">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs eller också är resursens värde inte ett heltals värde, eller så ryms inte heltalet i ett 32-bitars tal.</span><span class="sxs-lookup"><span data-stu-id="33f75-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="33f75-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="33f75-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="33f75-789">Hämta värdet för ett 64-bitars heltal flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-790">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-791">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-791">Description</span></span>

<span data-ttu-id="33f75-792">Tjänsten hämtar värdet för en 64-bitars heltals resurs instans från en flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-793">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-793">Parameters</span></span>

- <span data-ttu-id="33f75-794">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-795">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-796">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-797">**int64_ptr**: pekar mot målet 64-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-798">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-798">Return Values</span></span>

- <span data-ttu-id="33f75-799">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-800">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-801">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett heltals värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="33f75-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="33f75-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="33f75-803">Hämta värdet för en objekt länk flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-804">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-805">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-805">Description</span></span>

<span data-ttu-id="33f75-806">Tjänsten hämtar värdet för en objekt länk resurs instans från en flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-807">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-807">Parameters</span></span>

- <span data-ttu-id="33f75-808">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-809">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-810">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-811">**objlnk_ptr**: pekar mot länk värde för mål objekt.</span><span class="sxs-lookup"><span data-stu-id="33f75-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-812">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-812">Return Values</span></span>

- <span data-ttu-id="33f75-813">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-814">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-815">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett objekt länk värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="33f75-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="33f75-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="33f75-817">Hämta värdet för en täckande flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-818">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-819">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-819">Description</span></span>

<span data-ttu-id="33f75-820">Tjänsten hämtar värdet för en ogenomskinlig resurs instans från flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="33f75-821">Ett ogenomskinligt resurs värde består av en pekare till en buffert och en längd.</span><span class="sxs-lookup"><span data-stu-id="33f75-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-822">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-822">Parameters</span></span>

- <span data-ttu-id="33f75-823">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-824">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-825">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-826">**opaque_ptr_ptr**: pekar mot målets täckande buffer-pekare.</span><span class="sxs-lookup"><span data-stu-id="33f75-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="33f75-827">**opaque_length_ptr**: pekar mot målets täckande buffertlängd.</span><span class="sxs-lookup"><span data-stu-id="33f75-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-828">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-828">Return Values</span></span>

- <span data-ttu-id="33f75-829">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-830">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-831">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är resursens värde inte ett ogenomskinligt värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="33f75-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="33f75-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="33f75-833">Hämta värdet för en sträng flera resurs instanser</span><span class="sxs-lookup"><span data-stu-id="33f75-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="33f75-834">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33f75-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="33f75-835">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33f75-835">Description</span></span>

<span data-ttu-id="33f75-836">Tjänsten hämtar värdet för en sträng resurs instans från flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="33f75-837">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33f75-837">Parameters</span></span>

- <span data-ttu-id="33f75-838">**värde**: pekar mot värde beskrivning för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="33f75-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="33f75-839">**index**: index för den instans som ska hämtas i resurs värdes mat ris.</span><span class="sxs-lookup"><span data-stu-id="33f75-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="33f75-840">**instance_id_ptr**: pekar mot mål instansens ID.</span><span class="sxs-lookup"><span data-stu-id="33f75-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="33f75-841">**string_ptr_ptr**: pekar mot mål sträng pekaren.</span><span class="sxs-lookup"><span data-stu-id="33f75-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="33f75-842">**string_length_ptr**: pekar mot mål strängens längd.</span><span class="sxs-lookup"><span data-stu-id="33f75-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="33f75-843">Kan vara NULL om strängen är null-terminerad.</span><span class="sxs-lookup"><span data-stu-id="33f75-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="33f75-844">Retur värden</span><span class="sxs-lookup"><span data-stu-id="33f75-844">Return Values</span></span>

- <span data-ttu-id="33f75-845">**NX_SUCCESS**: åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="33f75-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="33f75-846">**NX_LWM2M_BAD_PARAMETER**: indexet ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="33f75-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="33f75-847">**NX_LWM2M_BAD_ENCODING**: resursen är inte en multipel resurs, eller så är instans svärdet inte ett sträng värde.</span><span class="sxs-lookup"><span data-stu-id="33f75-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
