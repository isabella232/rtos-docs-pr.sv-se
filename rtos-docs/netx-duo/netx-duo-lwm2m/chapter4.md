---
title: Kapitel 4 – Beskrivning av LWM2M klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla LWM2M klient tjänster i alfabetisk ordning.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825929"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="eea0d-103">Kapitel 4 Beskrivning av LWM2M-KLIENTtjänster</span><span class="sxs-lookup"><span data-stu-id="eea0d-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="eea0d-104">Det här kapitlet innehåller en beskrivning av alla LWM2M klient tjänster som listas nedan i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="eea0d-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="eea0d-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av  **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="eea0d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="eea0d-106">**LWM2M klient hantering:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="eea0d-107">nx_lwm2m_client_create: *skapa lwm2m-klient*</span><span class="sxs-lookup"><span data-stu-id="eea0d-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-108">nx_lwm2m_client_delete: *ta bort lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-109">nx_lwm2m_client_lock: *Lås lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-110">nx_lwm2m_client_unlock: *Lås upp lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="eea0d-111">**LWM2M för hantering av klient sessioner:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="eea0d-112">nx_lwm2m_client_session_create: *skapa en lwm2m-klientsession*</span><span class="sxs-lookup"><span data-stu-id="eea0d-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="eea0d-113">nx_lwm2m_client_session_delete: *ta bort lwm2m-klientsession*</span><span class="sxs-lookup"><span data-stu-id="eea0d-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="eea0d-114">nx_lwm2m_client_session_bootstrap: *starta en session med en Start Server*</span><span class="sxs-lookup"><span data-stu-id="eea0d-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="eea0d-115">nx_lwm2m_client_session_bootstrap_dtls: *starta en säker session med en Start Server*</span><span class="sxs-lookup"><span data-stu-id="eea0d-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="eea0d-116">nx_lwm2m_client_session_register_info_get: *Hämta Lwm2m Server register information*</span><span class="sxs-lookup"><span data-stu-id="eea0d-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="eea0d-117">nx_lwm2m_client_session_register: *starta en session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="eea0d-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="eea0d-118">nx_lwm2m_client_session_register_dtls: *starta en säker session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="eea0d-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="eea0d-119">nx_lwm2m_client_session_update: *Uppdatera en session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="eea0d-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="eea0d-120">nx_lwm2m_client_session_deregister: *Avsluta en session med en lwm2m-Server*</span><span class="sxs-lookup"><span data-stu-id="eea0d-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="eea0d-121">nx_lwm2m_client_session_error_get: *Hämta senaste fel i en session*</span><span class="sxs-lookup"><span data-stu-id="eea0d-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="eea0d-122">**Implementering av enhets objekt:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="eea0d-123">nx_lwm2m_client_device_callbacks_set: *Ange återanrop i enhets objekts program*</span><span class="sxs-lookup"><span data-stu-id="eea0d-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="eea0d-124">nx_lwm2m_client_device_error_push: *Lägg till felkod till enhets objekt*</span><span class="sxs-lookup"><span data-stu-id="eea0d-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="eea0d-125">nx_lwm2m_client_device_error_reset: *återställa felkoder för enhets objekt*</span><span class="sxs-lookup"><span data-stu-id="eea0d-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="eea0d-126">nx_lwm2m_client_device_resource_changed: *signal ändring av enhets objekt resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="eea0d-127">**Objekt implementering för uppdatering av inbyggd program vara:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="eea0d-128">nx_lwm2m_firmware_create: *skapa uppdaterings objekt för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="eea0d-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="eea0d-129">nx_lwm2m_firmware_package_info_set: *Ange information om uppdaterings paket för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="eea0d-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="eea0d-130">nx_lwm2m_firmware_result_set: *Ange uppdaterings resultat för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="eea0d-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="eea0d-131">nx_lwm2m_firmware_state_set: *Ange uppdaterings tillstånd för inbyggd program vara*</span><span class="sxs-lookup"><span data-stu-id="eea0d-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="eea0d-132">**Implementering av anpassade objekt:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="eea0d-133">nx_lwm2m_client_object_add: *Lägg till objekt implementering i lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-134">nx_lwm2m_client_object_remove: *ta bort objekt implementering från lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-135">nx_lwm2m_client_object_instance_add: *Lägg till objekt instans i lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-136">nx_lwm2m_client_object_instance_remove: *ta bort objekt instansen från lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-137">nx_lwm2m_object_resource_changed: *signal ändring av ett resurs värde för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="eea0d-138">**Hantering av lokala enheter**</span><span class="sxs-lookup"><span data-stu-id="eea0d-138">**Local Device Management**</span></span>

- <span data-ttu-id="eea0d-139">nx_lwm2m_client_object_create: *skapa en ny objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="eea0d-140">nx_lwm2m_client_object_delete: *ta bort en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="eea0d-141">nx_lwm2m_client_object_discover: *identifiera resurser för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="eea0d-142">nx_lwm2m_client_object_execute: *Kör resurs för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="eea0d-143">nx_lwm2m_client_object_next_get: *Hämta listan över objekt som implementeras av lwm2m-klienten*</span><span class="sxs-lookup"><span data-stu-id="eea0d-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="eea0d-144">nx_lwm2m_client_object_instance_next_get: *Hämta listan över instanser av ett objekt*</span><span class="sxs-lookup"><span data-stu-id="eea0d-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="eea0d-145">nx_lwm2m_client_object_read: *läsa resurs värden för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="eea0d-146">nx_lwm2m_client_object_write: *Ändra resurs värden för en objekt instans*</span><span class="sxs-lookup"><span data-stu-id="eea0d-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="eea0d-147">**Inställning av resurs information och värden:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="eea0d-148">nx_lwm2m_client_resource_info_set: *Ange resurs informationen*</span><span class="sxs-lookup"><span data-stu-id="eea0d-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="eea0d-149">nx_lwm2m_client_resource_string_set: *Ange resurs värde som sträng*</span><span class="sxs-lookup"><span data-stu-id="eea0d-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="eea0d-150">nx_lwm2m_client_resource_integer32_set: *Ange resurs värde som 32-bitars heltal*</span><span class="sxs-lookup"><span data-stu-id="eea0d-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="eea0d-151">nx_lwm2m_client_resource_integer64_set: *Ange resurs värde som 64-bitars heltal*</span><span class="sxs-lookup"><span data-stu-id="eea0d-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="eea0d-152">nx_lwm2m_client_resource_float32_set: *Ange resurs värde som 32-bitars flyttal*</span><span class="sxs-lookup"><span data-stu-id="eea0d-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="eea0d-153">nx_lwm2m_client_resource_float64_set: *Ange resurs värde som 64-bitars flyttal*</span><span class="sxs-lookup"><span data-stu-id="eea0d-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="eea0d-154">nx_lwm2m_client_resource_boolean_set: *Ange resurs värde som booleskt värde*</span><span class="sxs-lookup"><span data-stu-id="eea0d-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="eea0d-155">nx_lwm2m_client_resource_objlnk_set: *Ange resurs värde som objekt länk*</span><span class="sxs-lookup"><span data-stu-id="eea0d-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="eea0d-156">nx_lwm2m_client_resource_opaque_set: *Ange resurs värde som ogenomskinligt*</span><span class="sxs-lookup"><span data-stu-id="eea0d-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="eea0d-157">nx_lwm2m_client_resource_instance_set: *Ange resurs värde som instansen för flera resurser*</span><span class="sxs-lookup"><span data-stu-id="eea0d-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="eea0d-158">nx_lwm2m_client_resource_dim_set: *Ange resurs dimensionen för flera resurser.*</span><span class="sxs-lookup"><span data-stu-id="eea0d-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="eea0d-159">**Resurs information och värden får:**</span><span class="sxs-lookup"><span data-stu-id="eea0d-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="eea0d-160">nx_lwm2m_client_resource_info_get: *Hämta resursinformation*</span><span class="sxs-lookup"><span data-stu-id="eea0d-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="eea0d-161">nx_lwm2m_client_resource_string_get: *Hämta värdet för en sträng resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="eea0d-162">nx_lwm2m_client_resource_integer32_get: *Hämta värdet för en 32-bitars heltals resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="eea0d-163">nx_lwm2m_client_resource_integer64_get: *Hämta värdet för en 64-bitars heltals resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="eea0d-164">nx_lwm2m_client_resource_float32_get: *Hämta värdet för en 32-bitars float-resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="eea0d-165">nx_lwm2m_client_resource_float64_get: *Hämta värdet för en 64-bitars float-resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="eea0d-166">nx_lwm2m_client_resource_boolean_get: *Hämta värdet för en boolesk resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="eea0d-167">nx_lwm2m_client_resource_objlnk_get: *Hämta värdet för en objekt länk resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="eea0d-168">nx_lwm2m_client_resource_opaque_get: *Hämta värdet för en ogenomskinlig resurs*</span><span class="sxs-lookup"><span data-stu-id="eea0d-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="eea0d-169">nx_lwm2m_client_resource_instance_get: *Hämta resurs instansen för flera resurser*</span><span class="sxs-lookup"><span data-stu-id="eea0d-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="eea0d-170">nx_lwm2m_client_resource_dim_get: *Hämta resurs dimensionen för flera resurser.*</span><span class="sxs-lookup"><span data-stu-id="eea0d-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="eea0d-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="eea0d-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="eea0d-172">Skapar en LWM2M-klient.</span><span class="sxs-lookup"><span data-stu-id="eea0d-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="eea0d-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-174">Description</span></span>

<span data-ttu-id="eea0d-175">Den här tjänsten skapar en LWM2M-klient instans som körs i kontexten för en egen ThreadX-tråd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="eea0d-176">LWM2M-klienten implementerar följande OMA LWM2M-objekt: Security (0), Server (1), Access Control (2) och enhet (3).</span><span class="sxs-lookup"><span data-stu-id="eea0d-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="eea0d-177">Implementeringar av andra objekt måste läggas till av programmet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-178">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-178">Parameters</span></span>

- <span data-ttu-id="eea0d-179">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-180">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="eea0d-181">**packet_pool_ptr** Visar en pekare till LWM2M-klientens standardpool.</span><span class="sxs-lookup"><span data-stu-id="eea0d-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="eea0d-182">**name_ptr** Pekare till LWM2M-klientens slut punkts namn.</span><span class="sxs-lookup"><span data-stu-id="eea0d-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="eea0d-183">**name_length** Längden på LWM2M-klientens slut punkts namn.</span><span class="sxs-lookup"><span data-stu-id="eea0d-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="eea0d-184">**msisdn_ptr** Pekaren till MSISDN där LWM2M-klienten kan nås för användning med SMS-bindningen, kan vara NULL om SMS-bindning inte stöds.</span><span class="sxs-lookup"><span data-stu-id="eea0d-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="eea0d-185">**msisdn_length** Längd på MSISDN-nummer.</span><span class="sxs-lookup"><span data-stu-id="eea0d-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="eea0d-186">**binding_modes** Bindningen och lägena som stöds av LWM2M-klienten måste vara en kombination av NX_LWM2M_BINDING_U-, NX_LWM2M_BINDING_UQ-, NX_LWM2M_BINDING_S-och NX_LWM2M_BINDING_SQ flaggor.</span><span class="sxs-lookup"><span data-stu-id="eea0d-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="eea0d-187">**stack_ptr** Pekare till LWM2M klient tråds tack.</span><span class="sxs-lookup"><span data-stu-id="eea0d-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="eea0d-188">**stack_size** LWM2M klient trådens stack storlek.</span><span class="sxs-lookup"><span data-stu-id="eea0d-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="eea0d-189">**prioritet** Prioritet för LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-190">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-190">Return Values</span></span>

- <span data-ttu-id="eea0d-191">**NX_SUCCESS** LWM2M-klienten har skapats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="eea0d-192">**NX_LWM2M_CLIENT_ERROR** LWM2M-klient skapa fel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="eea0d-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="eea0d-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="eea0d-194">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="eea0d-195">**NX_SIZE_ERROR** Ogiltig stack storlek.</span><span class="sxs-lookup"><span data-stu-id="eea0d-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="eea0d-196">**NX_OPTION_ERROR** Ogiltig prioritet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-197">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-197">Allowed From</span></span>

<span data-ttu-id="eea0d-198">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-199">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="eea0d-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="eea0d-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="eea0d-201">Tar bort en LWM2M-klient.</span><span class="sxs-lookup"><span data-stu-id="eea0d-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-202">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-203">Description</span></span>

<span data-ttu-id="eea0d-204">Den här tjänsten tar bort en tidigare skapad LWM2M-klient instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="eea0d-205">Alla sessioner som är anslutna till klienten tas också bort av det här anropet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-206">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-206">Parameters</span></span>

- <span data-ttu-id="eea0d-207">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-208">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-208">Return Values</span></span>

- <span data-ttu-id="eea0d-209">**NX_SUCCESS** LWM2M-klienten har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="eea0d-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="eea0d-210">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-211">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-211">Allowed From</span></span>

<span data-ttu-id="eea0d-212">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-213">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="eea0d-214">nx_lwm2m_client_device_callback_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="eea0d-215">Anger ett enhets objekts återanrop för programmet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-216">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="eea0d-217">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-217">Description</span></span>

<span data-ttu-id="eea0d-218">Den här tjänsten installerar program återanrop för att implementera åtgärder på LWM2M enhets objekt resurser som inte hanteras av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="eea0d-219">LWM2M-klienten implementerar följande resurser: felkod (11), Reset-felkod (12) och bindning och lägen som stöds (16). åtgärder för de andra resurserna omdirigeras till programmet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-220">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-220">Parameters</span></span>

- <span data-ttu-id="eea0d-221">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-222">**operation_callback** Återanrop för "Read", "Discovery", "Write" och "EXECUTE".</span><span class="sxs-lookup"><span data-stu-id="eea0d-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-223">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-223">Return Values</span></span>

- <span data-ttu-id="eea0d-224">**NX_SUCCESS** Återanropet för åtgärden har angetts.</span><span class="sxs-lookup"><span data-stu-id="eea0d-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="eea0d-225">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-226">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-226">Allowed From</span></span>

<span data-ttu-id="eea0d-227">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-228">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="eea0d-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="eea0d-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="eea0d-230">Lägger till en felkod till ett enhets objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-231">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="eea0d-232">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-232">Description</span></span>

<span data-ttu-id="eea0d-233">Den här tjänsten lägger till en ny instans i fel kods resursen (11) för objekt enheten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-234">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-234">Parameters</span></span>

- <span data-ttu-id="eea0d-235">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-236">**kod** Den nya felkoden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-237">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-237">Return Values</span></span>

- <span data-ttu-id="eea0d-238">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="eea0d-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="eea0d-240">Det maximala antalet lagrade felkoder har</span><span class="sxs-lookup"><span data-stu-id="eea0d-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="eea0d-241">nåtts.</span><span class="sxs-lookup"><span data-stu-id="eea0d-241">been reached.</span></span>

<span data-ttu-id="eea0d-242">NX_PTR_ERROR ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-243">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-243">Allowed From</span></span>

<span data-ttu-id="eea0d-244">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-245">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="eea0d-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="eea0d-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="eea0d-247">Återställer felkoden för enhets objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-248">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-249">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-249">Description</span></span>

<span data-ttu-id="eea0d-250">Den här tjänsten tar bort alla fel kods resurs instanser från objektet enhet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="eea0d-251">Det motsvarar att köra fel koden för resurs återställning (12).</span><span class="sxs-lookup"><span data-stu-id="eea0d-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-252">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-252">Parameters</span></span>

- <span data-ttu-id="eea0d-253">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-254">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-254">Return Values</span></span>

- <span data-ttu-id="eea0d-255">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-256">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-257">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-257">Allowed From</span></span>

<span data-ttu-id="eea0d-258">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-259">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="eea0d-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="eea0d-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="eea0d-261">Signalerar en ändring av en enhets objekt resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-262">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="eea0d-263">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-263">Description</span></span>

<span data-ttu-id="eea0d-264">Tjänsten används av programmet för att signalera till LWM2M-klienten att en resurs av objekt enheten har ändrats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="eea0d-265">LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-266">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-266">Parameters</span></span>

- <span data-ttu-id="eea0d-267">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-268">**resurs** Pekar till strukturen som beskriver den resurs som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-269">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-269">Return Values</span></span>

- <span data-ttu-id="eea0d-270">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-271">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-272">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-272">Allowed From</span></span>

<span data-ttu-id="eea0d-273">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-274">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="eea0d-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="eea0d-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="eea0d-276">Skapa ett LWM2M-klient-objekt för inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="eea0d-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="eea0d-277">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="eea0d-278">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-278">Description</span></span>

<span data-ttu-id="eea0d-279">Tjänsten används av programmet för att skapa en inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="eea0d-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-280">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-280">Parameters</span></span>

- <span data-ttu-id="eea0d-281">**firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="eea0d-282">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-283">**protokoll** Protokoll som stöds.</span><span class="sxs-lookup"><span data-stu-id="eea0d-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="eea0d-284">**package_callback** Paket återanropet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="eea0d-285">**package_uri_callback** Paket-URI-motanrop.</span><span class="sxs-lookup"><span data-stu-id="eea0d-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="eea0d-286">**update_callback** Återanropet för uppdateringen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-287">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-287">Return Values</span></span>

<span data-ttu-id="eea0d-288">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="eea0d-289">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-290">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-290">Allowed From</span></span>

<span data-ttu-id="eea0d-291">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-292">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="eea0d-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="eea0d-294">Anger information om LWM2M-klientens firmware-paket.</span><span class="sxs-lookup"><span data-stu-id="eea0d-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-295">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="eea0d-296">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-296">Description</span></span>

<span data-ttu-id="eea0d-297">Tjänsten används av programmet för att ange paket informations resurserna för det inbyggda program varans uppdaterings objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-298">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-298">Parameters</span></span>

- <span data-ttu-id="eea0d-299">**firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="eea0d-300">**namn** Namnet på den inbyggda program varans paket.</span><span class="sxs-lookup"><span data-stu-id="eea0d-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="eea0d-301">**name_length** Namnets längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="eea0d-302">**version** Versionen av den inbyggda program varans paket.</span><span class="sxs-lookup"><span data-stu-id="eea0d-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="eea0d-303">**version_length** Versionens längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-304">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-304">Return Values</span></span>

- <span data-ttu-id="eea0d-305">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-306">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-307">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-307">Allowed From</span></span>

<span data-ttu-id="eea0d-308">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-309">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="eea0d-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="eea0d-311">Anger uppdaterings resultat resursen för det inbyggda program varans uppdaterings objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-312">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="eea0d-313">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-313">Description</span></span>

<span data-ttu-id="eea0d-314">Tjänsten används av programmet för att ställa in uppdaterings resultat resursen för objektet för den inbyggda program varan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-315">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-315">Parameters</span></span>

- <span data-ttu-id="eea0d-316">**firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="eea0d-317">**resultat** Uppdaterings resultatet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-318">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-318">Return Values</span></span>

- <span data-ttu-id="eea0d-319">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-320">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-321">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-321">Allowed From</span></span>

<span data-ttu-id="eea0d-322">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-323">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="eea0d-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="eea0d-325">Anger uppdaterings resultat resursen för det inbyggda program varans uppdaterings objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-326">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="eea0d-327">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-327">Description</span></span>

<span data-ttu-id="eea0d-328">Tjänsten används av programmet för att ange tillstånd för uppdaterings objekt för den inbyggda program varan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-329">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-329">Parameters</span></span>

- <span data-ttu-id="eea0d-330">**firmware_ptr** Pekare till LWM2M-klientens inbyggda objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="eea0d-331">**tillstånd** Status för den inbyggda program varans objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-332">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-332">Return Values</span></span>

- <span data-ttu-id="eea0d-333">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-334">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-335">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-335">Allowed From</span></span>

<span data-ttu-id="eea0d-336">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-337">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="eea0d-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="eea0d-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="eea0d-339">Låser LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-340">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-341">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-341">Description</span></span>

<span data-ttu-id="eea0d-342">Den här tjänsten låser LWM2M-klienten för att förhindra samtidig åtkomst till LWM2M-objekt från servrar eller en annan program tråd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="eea0d-343">Om LWM2M-klienten är låst av en annan tråd, kommer funktionen att blockeras tills LWM2M-klienten har låsts upp.</span><span class="sxs-lookup"><span data-stu-id="eea0d-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="eea0d-344">Anrop till \***nx_lwm2m_client_lock** _/_ \*_nx_lwm2m_client_unlock_\*\*-par kan kapslas.</span><span class="sxs-lookup"><span data-stu-id="eea0d-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-345">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-345">Parameters</span></span>

- <span data-ttu-id="eea0d-346">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-347">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-347">Return Values</span></span>

- <span data-ttu-id="eea0d-348">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-349">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-350">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-350">Allowed From</span></span>

<span data-ttu-id="eea0d-351">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-352">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="eea0d-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="eea0d-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="eea0d-354">Lägger till en objekt implementering i LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-355">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="eea0d-356">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-356">Description</span></span>

<span data-ttu-id="eea0d-357">Den här tjänsten lägger till en ny objekt implementering i LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-358">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-358">Parameters</span></span>

- <span data-ttu-id="eea0d-359">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-360">**object_ptr** Pekare till strukturen som definierar objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="eea0d-361">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-361">**object_id** The object id.</span></span>
- <span data-ttu-id="eea0d-362">**object_operation** Funktionen motringning för objekt åtgärd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-363">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-363">Return Values</span></span>

- <span data-ttu-id="eea0d-364">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID: t finns redan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="eea0d-366">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-367">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-367">Allowed From</span></span>

<span data-ttu-id="eea0d-368">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-369">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="eea0d-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="eea0d-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="eea0d-371">Skapar en ny objekt instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-372">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-373">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-373">Description</span></span>

<span data-ttu-id="eea0d-374">Den här tjänsten utför en "skapa"-åtgärd på ett objekt av LWM2M-klienten för att skapa en ny objekt instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-375">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-375">Parameters</span></span>

- <span data-ttu-id="eea0d-376">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-377">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-378">**instance_id_ptr** Pekaren till ID: t för den nya instansen kan vara **Null** om LWM2M-klienten måste tilldela ett instans-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="eea0d-379">Om ID: t är det reserverade värdet 65535, tilldelar LWM2M-klienten ett instans-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="eea0d-380">Om det tilldelade ID: t inte är NULL returneras det efter anropet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="eea0d-381">**num_values** Antalet värden som ska anges.</span><span class="sxs-lookup"><span data-stu-id="eea0d-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="eea0d-382">**values_ptr** Pekar mot en matris med resurs värden för att initiera den nya objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-383">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-383">Return Values</span></span>

- <span data-ttu-id="eea0d-384">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt instans-ID: t finns redan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="eea0d-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Objektet har inte stöd för att skapa en instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="eea0d-387">**NX_LWM2M_CLIENT_NO_MEMORY** Det går inte att allokera minne för att lagra den nya instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="eea0d-388">**NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t finns inte.</span><span class="sxs-lookup"><span data-stu-id="eea0d-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="eea0d-389">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-390">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-390">Allowed From</span></span>

<span data-ttu-id="eea0d-391">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-392">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="eea0d-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="eea0d-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="eea0d-394">Tar bort en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-395">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="eea0d-396">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-396">Description</span></span>

<span data-ttu-id="eea0d-397">Den här tjänsten utför en borttagnings åtgärd på en objekt instans av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-398">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-398">Parameters</span></span>

- <span data-ttu-id="eea0d-399">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-400">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-401">**instance_id** Objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-402">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-402">Return Values</span></span>

- <span data-ttu-id="eea0d-403">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Objektet har inte stöd för borttagning av instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="eea0d-405">**NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t eller objekt instans-ID: t finns inte.</span><span class="sxs-lookup"><span data-stu-id="eea0d-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="eea0d-406">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-407">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-407">Allowed From</span></span>

<span data-ttu-id="eea0d-408">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-409">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="eea0d-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="eea0d-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="eea0d-411">Identifierar resurser för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-412">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="eea0d-413">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-413">Description</span></span>

<span data-ttu-id="eea0d-414">Den här tjänsten utför en "Discover"-åtgärd på en objekt instans av LWM2M-klienten, vilket returnerar listan över resurser som implementeras av objektet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-415">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-415">Parameters</span></span>

- <span data-ttu-id="eea0d-416">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-417">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-418">**instance_id** Objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="eea0d-419">**num_resources** Vid indata anger du storleken på målcachen vid utdata av antalet element som skrivs till bufferten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="eea0d-420">**resurser** Pekar mot målcachen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-421">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-421">Return Values</span></span>

- <span data-ttu-id="eea0d-422">*NX_SUCCESS*\* åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="eea0d-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Resursens buffert är för liten för att lagra listan över resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="eea0d-424">**NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t eller objekt instans-ID: t finns inte.</span><span class="sxs-lookup"><span data-stu-id="eea0d-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="eea0d-425">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-426">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-426">Allowed From</span></span>

<span data-ttu-id="eea0d-427">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-428">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="eea0d-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="eea0d-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="eea0d-430">Utför en körnings åtgärd på en resurs av en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-431">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="eea0d-432">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-432">Description</span></span>

<span data-ttu-id="eea0d-433">Den här tjänsten utför åtgärden kör på en objekt instans resurs för LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-434">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-434">Parameters</span></span>

- <span data-ttu-id="eea0d-435">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-436">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-437">**instance_id** Objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="eea0d-438">**resource_id** Resurs-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="eea0d-439">**arguments_ptr** Pekar till argumenten för körnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="eea0d-440">Kan vara NULL om arguments_length är noll.</span><span class="sxs-lookup"><span data-stu-id="eea0d-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="eea0d-441">**arguments_length** Argumentens längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-442">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-442">Return Values</span></span>

- <span data-ttu-id="eea0d-443">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Resursens buffert är för liten för att lagra listan över resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="eea0d-445">**NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID: t eller objekt instans-ID: t finns inte.</span><span class="sxs-lookup"><span data-stu-id="eea0d-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="eea0d-446">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-447">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-447">Allowed From</span></span>

<span data-ttu-id="eea0d-448">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-449">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="eea0d-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="eea0d-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="eea0d-451">Lägger till en objekt instans implementering till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-452">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-453">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-453">Description</span></span>

<span data-ttu-id="eea0d-454">Den här tjänsten lägger till en ny implementering av objekt instansen i LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="eea0d-455">Om värdet för instance_id_ptr är **NX_LWM2M_CLIENT_RESERVED_ID** tilldelar LWM2M-klienten automatiskt ett oanvänt instans-ID, annars kommer LWM2M-klienten att använda värdet program uppsättning.</span><span class="sxs-lookup"><span data-stu-id="eea0d-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="eea0d-456">När den nya instansen har lagts till kommer instance_id att fyllas i instance_id_ptr att återgå till programmet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-457">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-457">Parameters</span></span>

- <span data-ttu-id="eea0d-458">**object_ptr** Pekare till strukturen som definierar objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="eea0d-459">**instance_ptr** Pekare till strukturen som definierar implementeringen av objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="eea0d-460">**instance_id_ptr** Pekare till objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-461">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-461">Return Values</span></span>

- <span data-ttu-id="eea0d-462">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** Objekt-ID: t finns redan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="eea0d-464">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-465">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-465">Allowed From</span></span>

<span data-ttu-id="eea0d-466">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-467">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="eea0d-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="eea0d-469">Hämtar nästa instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-470">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-471">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-471">Description</span></span>

<span data-ttu-id="eea0d-472">Den här tjänsten returnerar ID: t för nästa objekt instans av det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="eea0d-473">Om det aktuella instans-ID: t är inställt på NX_LWM2M_RESERVED_ID (65535) returneras ID: t för den första instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-474">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-474">Parameters</span></span>

- <span data-ttu-id="eea0d-475">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-476">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-477">**instance_id_ptr** Pekar mot det aktuella objekt instans-ID: t.</span><span class="sxs-lookup"><span data-stu-id="eea0d-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="eea0d-478">Vid retur innehåller nästa instans-ID för objektet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-479">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-479">Return Values</span></span>

- <span data-ttu-id="eea0d-480">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-481">**NX_CLIENT_LWM2M_NOT_FOUND** Angivet instans-ID är det sista objektet eller objekt-ID: t är inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="eea0d-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="eea0d-482">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-483">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-483">Allowed From</span></span>

<span data-ttu-id="eea0d-484">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-485">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="eea0d-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="eea0d-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="eea0d-487">Tar bort en objekt instans implementering från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-488">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-489">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-489">Description</span></span>

<span data-ttu-id="eea0d-490">Den här tjänsten tar bort en objekt instans från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-491">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-491">Parameters</span></span>

- <span data-ttu-id="eea0d-492">***object_ptr*** Pekare till strukturen som definierar objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="eea0d-493">**instance_ptr** Pekare till strukturen som definierar implementeringen av objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-494">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-494">Return Values</span></span>

- <span data-ttu-id="eea0d-495">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID: t finns redan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="eea0d-497">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-498">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-498">Allowed From</span></span>

<span data-ttu-id="eea0d-499">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-500">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="eea0d-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="eea0d-502">Hämtar nästa objekt för LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-503">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-504">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-504">Description</span></span>

<span data-ttu-id="eea0d-505">Den här tjänsten returnerar ID: t för nästa objekt som implementeras av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="eea0d-506">Om aktuellt objekt-ID är inställt på NX_LWM2M_RESERVED_ID (65535) returneras det första objekt-ID: t.</span><span class="sxs-lookup"><span data-stu-id="eea0d-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-507">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-507">Parameters</span></span>

- <span data-ttu-id="eea0d-508">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-509">**object_id_ptr** Pekar mot aktuellt objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="eea0d-510">Vid retur innehåller nästa objekt-ID som implementeras av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-511">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-511">Return Values</span></span>

- <span data-ttu-id="eea0d-512">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-513">**NX_LWM2M_CLIENT_NOT_FOUND** Angivet objekt-ID är det sista i databasen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="eea0d-514">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-515">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-515">Allowed From</span></span>

<span data-ttu-id="eea0d-516">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-517">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="eea0d-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="eea0d-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="eea0d-519">Läser en objekt Instanss resource's-värden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-520">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="eea0d-521">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-521">Description</span></span>

<span data-ttu-id="eea0d-522">Den här tjänsten utför en Läs åtgärd på en objekt instans av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-523">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-523">Parameters</span></span>

- <span data-ttu-id="eea0d-524">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-525">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-526">**instance_id** Objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="eea0d-527">**num_values** Antalet resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="eea0d-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="eea0d-528">**values_ptr** Pekar till en matris med NX_LWM2M_RESOURCE som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="eea0d-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="eea0d-529">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-530">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-530">Return Values</span></span>

- <span data-ttu-id="eea0d-531">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** En resurs har inte stöd för Läs åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="eea0d-533">**NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID, objekt instans-ID eller resurs-ID finns inte.</span><span class="sxs-lookup"><span data-stu-id="eea0d-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="eea0d-534">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-535">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-535">Allowed From</span></span>

<span data-ttu-id="eea0d-536">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-537">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="eea0d-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="eea0d-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="eea0d-539">Tar bort en objekt instans implementering från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-540">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-541">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-541">Description</span></span>

<span data-ttu-id="eea0d-542">Den här tjänsten tar bort ett objekt från LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-543">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-543">Parameters</span></span>

- <span data-ttu-id="eea0d-544">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-545">**object_ptr** Pekare till strukturen som definierar objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-546">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-546">Return Values</span></span>

- <span data-ttu-id="eea0d-547">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** Objekt-ID: t finns redan.</span><span class="sxs-lookup"><span data-stu-id="eea0d-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="eea0d-549">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="eea0d-550">**NX_LWM2M_CLIENT_FORBIDDEN** Borttagning av internt objekt är förbjudet.</span><span class="sxs-lookup"><span data-stu-id="eea0d-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-551">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-551">Allowed From</span></span>

<span data-ttu-id="eea0d-552">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-553">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="eea0d-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="eea0d-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="eea0d-555">Signalerar en ändring av en objekt resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-556">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="eea0d-557">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-557">Description</span></span>

<span data-ttu-id="eea0d-558">Tjänsten används av programmet för att signalera till LWM2M-klienten om att en resurs objekt har ändrats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="eea0d-559">LWM2M-klienten skickar ett meddelande om resursen observeras av en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-560">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-560">Parameters</span></span>

- <span data-ttu-id="eea0d-561">**object_ptr** Pekare till strukturen som definierar objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="eea0d-562">***instance_ptr*** Pekare till strukturen som definierar implementeringen av objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="eea0d-563">**resurs** Pekar till strukturen som beskriver den resurs som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-564">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-564">Return Values</span></span>

- <span data-ttu-id="eea0d-565">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-566">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-567">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-567">Allowed From</span></span>

<span data-ttu-id="eea0d-568">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-569">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="eea0d-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="eea0d-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="eea0d-571">Ändrar resursens värden för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-572">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="eea0d-573">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-573">Description</span></span>

<span data-ttu-id="eea0d-574">Den här tjänsten utför en Skriv åtgärd på en objekt instans av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="eea0d-575">Följande Skriv åtgärder kan anges för parametern *write_op* .</span><span class="sxs-lookup"><span data-stu-id="eea0d-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="eea0d-576">Värde</span><span class="sxs-lookup"><span data-stu-id="eea0d-576">Value</span></span> | <span data-ttu-id="eea0d-577">Skriv &nbsp; åtgärd</span><span class="sxs-lookup"><span data-stu-id="eea0d-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="eea0d-578">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="eea0d-579">0</span><span class="sxs-lookup"><span data-stu-id="eea0d-579">0</span></span> | <span data-ttu-id="eea0d-580">Partiell uppdatering</span><span class="sxs-lookup"><span data-stu-id="eea0d-580">Partial Update</span></span> | <span data-ttu-id="eea0d-581">Lägger till eller uppdaterar resurser som finns i det nya värdet och lämnar andra befintliga resurser oförändrade.</span><span class="sxs-lookup"><span data-stu-id="eea0d-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="eea0d-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="eea0d-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="eea0d-583">Ersätt instans</span><span class="sxs-lookup"><span data-stu-id="eea0d-583">Replace Instance</span></span> | <span data-ttu-id="eea0d-584">Ersätter objekt instansen med de nya angivna resurs värdena.</span><span class="sxs-lookup"><span data-stu-id="eea0d-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="eea0d-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="eea0d-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="eea0d-586">Ersätt resurs</span><span class="sxs-lookup"><span data-stu-id="eea0d-586">Replace Resource</span></span> | <span data-ttu-id="eea0d-587">Ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser).</span><span class="sxs-lookup"><span data-stu-id="eea0d-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="eea0d-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="eea0d-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="eea0d-589">Bootstrap-skrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-589">Bootstrap Write</span></span> | <span data-ttu-id="eea0d-590">Anger ett anrop från en bootstrap-sekvens.</span><span class="sxs-lookup"><span data-stu-id="eea0d-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="eea0d-591">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-591">Parameters</span></span>

- <span data-ttu-id="eea0d-592">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="eea0d-593">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="eea0d-594">**instance_id** Objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="eea0d-595">**num_values** Antalet resurser som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="eea0d-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="eea0d-596">**values_ptr** Pekar till en matris med NX_LWM2M_RESOURCE som innehåller ID: n för resurserna, typerna och värdena som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="eea0d-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="eea0d-597">**write_op** Typ av Skriv åtgärd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-598">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-598">Return Values</span></span>

- <span data-ttu-id="eea0d-599">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-600">**NX_LWM2M_CLIENT_BAD_ENCODING** Resurs typen är inte giltig.</span><span class="sxs-lookup"><span data-stu-id="eea0d-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="eea0d-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Längden på ett värde är för stor för att lagras i instansen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="eea0d-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** En resurs har inte stöd för Skriv åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="eea0d-603">**NX_LWM2M_CLIENT_NO_MEMORY** Det går inte att allokera minne för att lagra ett resurs värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="eea0d-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Värdet för en resurs är inte giltigt.</span><span class="sxs-lookup"><span data-stu-id="eea0d-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="eea0d-605">**NX_LWM2M_CLIENT_NOT_FOUND** Objekt-ID, objekt instans-ID eller resurs-ID finns inte.</span><span class="sxs-lookup"><span data-stu-id="eea0d-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="eea0d-606">**NX_OPTION_ERROR** Ogiltig typ av Skriv åtgärd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="eea0d-607">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-608">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-608">Allowed From</span></span>

<span data-ttu-id="eea0d-609">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-610">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="eea0d-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="eea0d-612">Hämtar värdet för en boolesk resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-613">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-614">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-614">Description</span></span>

<span data-ttu-id="eea0d-615">Tjänsten hämtar värdet för en boolesk resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-616">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-616">Parameters</span></span>

- <span data-ttu-id="eea0d-617">**resurs** Pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="eea0d-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="eea0d-618">**bool_ptr** Pekar mot målets booleska värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-619">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-619">Return Values</span></span>

- <span data-ttu-id="eea0d-620">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-621">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="eea0d-622">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-623">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-623">Allowed From</span></span>

<span data-ttu-id="eea0d-624">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-625">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="eea0d-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="eea0d-627">Anger värdet för en boolesk resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-628">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="eea0d-629">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-629">Description</span></span>

<span data-ttu-id="eea0d-630">Tjänsten anger värdet för en boolesk resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-631">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-631">Parameters</span></span>

- <span data-ttu-id="eea0d-632">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-633">**bool_data** Booleska data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-634">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-634">Return Values</span></span>

- <span data-ttu-id="eea0d-635">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-636">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-637">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-637">Allowed From</span></span>

<span data-ttu-id="eea0d-638">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-639">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="eea0d-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="eea0d-641">Hämtar resurs dimensionen för flera resurser</span><span class="sxs-lookup"><span data-stu-id="eea0d-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-642">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="eea0d-643">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-643">Description</span></span>

<span data-ttu-id="eea0d-644">Tjänsten hämtar resurs dimensionen för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-645">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-645">Parameters</span></span>

- <span data-ttu-id="eea0d-646">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-647">**dim** pekare till mål dimensionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-648">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-648">Return Values</span></span>

- <span data-ttu-id="eea0d-649">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-650">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="eea0d-651">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-652">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-652">Allowed From</span></span>

<span data-ttu-id="eea0d-653">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-654">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="eea0d-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="eea0d-656">Anger resurs dimensionen för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-657">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="eea0d-658">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-658">Description</span></span>

<span data-ttu-id="eea0d-659">Tjänsten anger resurs dimensionen för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-660">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-660">Parameters</span></span>

- <span data-ttu-id="eea0d-661">**värde** Pekare till resurs värde beskrivning.</span><span class="sxs-lookup"><span data-stu-id="eea0d-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="eea0d-662">dimensions värde för **dimension** .</span><span class="sxs-lookup"><span data-stu-id="eea0d-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-663">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-663">Return Values</span></span>

- <span data-ttu-id="eea0d-664">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-665">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-666">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-666">Allowed From</span></span>

<span data-ttu-id="eea0d-667">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-668">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="eea0d-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="eea0d-670">Hämtar värdet för en 32-bitars **float** -resurs</span><span class="sxs-lookup"><span data-stu-id="eea0d-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-671">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-672">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-672">Description</span></span>

<span data-ttu-id="eea0d-673">Tjänsten hämtar värdet för en 32-bitars **float** -resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-674">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-674">Parameters</span></span>

- <span data-ttu-id="eea0d-675">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-676">**float32_ptr** Pekar till målet 32-bit **flytt ALS** värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-677">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-677">Return Values</span></span>

- <span data-ttu-id="eea0d-678">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-679">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="eea0d-680">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-681">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-681">Allowed From</span></span>

<span data-ttu-id="eea0d-682">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-683">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="eea0d-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="eea0d-685">Anger värdet för en 32-bitars **float** -resurs</span><span class="sxs-lookup"><span data-stu-id="eea0d-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-686">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="eea0d-687">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-687">Description</span></span>

<span data-ttu-id="eea0d-688">Tjänsten anger värdet för en 32-bitars **float** -resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-689">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-689">Parameters</span></span>

- <span data-ttu-id="eea0d-690">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-691">**float32_data** 32-bitars **float** -data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-692">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-692">Return Values</span></span>

- <span data-ttu-id="eea0d-693">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-694">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-695">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-695">Allowed From</span></span>

<span data-ttu-id="eea0d-696">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-697">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="eea0d-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="eea0d-699">Hämtar värdet för en 64-bitars float-resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-700">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-701">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-701">Description</span></span>

<span data-ttu-id="eea0d-702">Tjänsten hämtar värdet för en 64-bitars **float** -resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-703">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-703">Parameters</span></span>

- <span data-ttu-id="eea0d-704">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-705">**float64_ptr** Pekar till målet 64-bit **flytt ALS** värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-706">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-706">Return Values</span></span>

- <span data-ttu-id="eea0d-707">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-708">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett flytt ALS värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="eea0d-709">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-710">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-710">Allowed From</span></span>

<span data-ttu-id="eea0d-711">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-712">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="eea0d-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="eea0d-714">Anger värdet för en 64-bitars **float** -resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-715">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="eea0d-716">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-716">Description</span></span>

<span data-ttu-id="eea0d-717">Tjänsten anger värdet för en 64-bitars **float** -resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-718">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-718">Parameters</span></span>

- <span data-ttu-id="eea0d-719">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-720">**float64_data** 64-bitars **float** -data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-721">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-721">Return Values</span></span>

- <span data-ttu-id="eea0d-722">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-723">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-724">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-724">Allowed From</span></span>

<span data-ttu-id="eea0d-725">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-726">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="eea0d-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="eea0d-728">Hämtar resurs informationen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-729">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="eea0d-730">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-730">Description</span></span>

<span data-ttu-id="eea0d-731">Tjänsten hämtar resurs informationen för resursen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-732">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-732">Parameters</span></span>

- <span data-ttu-id="eea0d-733">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-734">**resource_id** Pekare till mål resurs-ID: t.</span><span class="sxs-lookup"><span data-stu-id="eea0d-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="eea0d-735">**åtgärd** Pekare till mål resurs åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eea0d-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-736">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-736">Return Values</span></span>

- <span data-ttu-id="eea0d-737">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-738">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-739">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-739">Allowed From</span></span>

<span data-ttu-id="eea0d-740">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-741">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="eea0d-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="eea0d-743">Anger resursinformation.</span><span class="sxs-lookup"><span data-stu-id="eea0d-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-744">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="eea0d-745">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-745">Description</span></span>

<span data-ttu-id="eea0d-746">Tjänsten anger resursinformationen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-747">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-747">Parameters</span></span>

- <span data-ttu-id="eea0d-748">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-749">**resource_id** Resursens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="eea0d-750">**åtgärd** Driften av resursen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-751">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-751">Return Values</span></span>

- <span data-ttu-id="eea0d-752">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-753">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-754">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-754">Allowed From</span></span>

<span data-ttu-id="eea0d-755">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-756">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="eea0d-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="eea0d-758">Hämtar instansen av flera resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-759">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="eea0d-760">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-760">Description</span></span>

<span data-ttu-id="eea0d-761">Tjänsten hämtar resurs informationen för resursen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-762">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-762">Parameters</span></span>

- <span data-ttu-id="eea0d-763">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-764">**resource_instances** Pekare till mål resurs-ID: t.</span><span class="sxs-lookup"><span data-stu-id="eea0d-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="eea0d-765">**antal** Pekar mot Count.</span><span class="sxs-lookup"><span data-stu-id="eea0d-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-766">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-766">Return Values</span></span>

- <span data-ttu-id="eea0d-767">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-768">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="eea0d-769">**NX_LWM2M_CLIENT_NO_MEMORY** Det fanns inte tillräckligt med minne för att fylla i instanser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="eea0d-770">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-771">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-771">Allowed From</span></span>

<span data-ttu-id="eea0d-772">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-773">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="eea0d-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="eea0d-775">Anger resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-776">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="eea0d-777">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-777">Description</span></span>

<span data-ttu-id="eea0d-778">Tjänsten anger resurs instanserna för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-779">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-779">Parameters</span></span>

- <span data-ttu-id="eea0d-780">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-781">**resource_instance** Pekare till resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="eea0d-782">**antal** Antal resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="eea0d-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-783">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-783">Return Values</span></span>

- <span data-ttu-id="eea0d-784">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-785">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-786">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-786">Allowed From</span></span>

<span data-ttu-id="eea0d-787">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-788">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="eea0d-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="eea0d-790">Hämtar värdet för en 32-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-791">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-792">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-792">Description</span></span>

<span data-ttu-id="eea0d-793">Tjänsten hämtar värdet för en 32-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-794">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-794">Parameters</span></span>

- <span data-ttu-id="eea0d-795">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-796">**integer32_ptr** Pekar mot 32-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-797">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-797">Return Values</span></span>

- <span data-ttu-id="eea0d-798">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-799">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett heltals värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="eea0d-800">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-801">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-801">Allowed From</span></span>

<span data-ttu-id="eea0d-802">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-803">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="eea0d-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="eea0d-805">Anger värdet för en 32-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-806">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="eea0d-807">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-807">Description</span></span>

<span data-ttu-id="eea0d-808">Tjänsten anger värdet för en 32-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-809">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-809">Parameters</span></span>

- <span data-ttu-id="eea0d-810">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-811">**integer32_data** 32-bitars heltals data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-812">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-812">Return Values</span></span>

- <span data-ttu-id="eea0d-813">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-814">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-815">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-815">Allowed From</span></span>

<span data-ttu-id="eea0d-816">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-817">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="eea0d-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="eea0d-819">Hämtar värdet för en 64-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-820">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-821">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-821">Description</span></span>

<span data-ttu-id="eea0d-822">Tjänsten hämtar värdet för en 64-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-823">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-823">Parameters</span></span>

- <span data-ttu-id="eea0d-824">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-825">**integer64_ptr** Pekar mot 64-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-826">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-826">Return Values</span></span>

- <span data-ttu-id="eea0d-827">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-828">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte 64-bitars heltals värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="eea0d-829">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-830">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-830">Allowed From</span></span>

<span data-ttu-id="eea0d-831">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-832">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="eea0d-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="eea0d-834">Ange värdet för en 64-bitars heltals resurs</span><span class="sxs-lookup"><span data-stu-id="eea0d-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-835">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="eea0d-836">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-836">Description</span></span>

<span data-ttu-id="eea0d-837">Tjänsten anger värdet för en 64-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-838">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-838">Parameters</span></span>

- <span data-ttu-id="eea0d-839">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-840">**integer64_data** 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="eea0d-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-841">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-841">Return Values</span></span>

- <span data-ttu-id="eea0d-842">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-843">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-844">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-844">Allowed From</span></span>

<span data-ttu-id="eea0d-845">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-846">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="eea0d-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="eea0d-848">Hämtar värdet för en objekt länk resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-849">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="eea0d-850">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-850">Description</span></span>

<span data-ttu-id="eea0d-851">Tjänsten hämtar värdet för objekt länken.</span><span class="sxs-lookup"><span data-stu-id="eea0d-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-852">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-852">Parameters</span></span>

- <span data-ttu-id="eea0d-853">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-854">**object_id** Pekar mot objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="eea0d-855">**instance_id** Pekare till objekt instansens ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-856">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-856">Return Values</span></span>

- <span data-ttu-id="eea0d-857">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-858">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett objekt länk värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="eea0d-859">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-860">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-860">Allowed From</span></span>

<span data-ttu-id="eea0d-861">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-862">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="eea0d-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="eea0d-864">Anger resurs instanser</span><span class="sxs-lookup"><span data-stu-id="eea0d-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-865">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="eea0d-866">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-866">Description</span></span>

<span data-ttu-id="eea0d-867">Tjänsten anger värdet för objekt länk resursen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-868">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-868">Parameters</span></span>

- <span data-ttu-id="eea0d-869">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-870">**object_id** Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="eea0d-871">**instance_id** Objekt instans-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-872">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-872">Return Values</span></span>

- <span data-ttu-id="eea0d-873">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-874">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-875">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-875">Allowed From</span></span>

<span data-ttu-id="eea0d-876">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-877">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="eea0d-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="eea0d-879">Hämtar värdet för en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-880">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="eea0d-881">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-881">Description</span></span>

<span data-ttu-id="eea0d-882">Tjänsten hämtar värdet för en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="eea0d-883">Ett ogenomskinligt resurs värde består av en pekare till en buffert och en längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-884">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-884">Parameters</span></span>

- <span data-ttu-id="eea0d-885">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-886">**opaque_ptr** Pekar mot täckande data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="eea0d-887">**opaque_length** Pekar mot ogenomskinlig data längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-888">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-888">Return Values</span></span>

- <span data-ttu-id="eea0d-889">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-890">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="eea0d-891">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-892">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-892">Allowed From</span></span>

<span data-ttu-id="eea0d-893">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-894">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="eea0d-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="eea0d-896">Anger värdet för en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-897">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="eea0d-898">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-898">Description</span></span>

<span data-ttu-id="eea0d-899">Tjänsten anger värdet för en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-900">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-900">Parameters</span></span>

- <span data-ttu-id="eea0d-901">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-902">**opaque_ptr** Pekar mot täckande data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="eea0d-903">**opaque_length** Längden på täckande data.</span><span class="sxs-lookup"><span data-stu-id="eea0d-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-904">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-904">Return Values</span></span>

- <span data-ttu-id="eea0d-905">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-906">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-907">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-907">Allowed From</span></span>

<span data-ttu-id="eea0d-908">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-909">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="eea0d-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="eea0d-911">Hämtar värdet för en sträng resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-912">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="eea0d-913">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-913">Description</span></span>

<span data-ttu-id="eea0d-914">Tjänsten hämtar värdet för en sträng resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-915">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-915">Parameters</span></span>

- <span data-ttu-id="eea0d-916">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-917">**string_ptr** Pekare till mål sträng pekaren.</span><span class="sxs-lookup"><span data-stu-id="eea0d-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="eea0d-918">**string_length** Pekar mot mål strängens längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="eea0d-919">Kan vara **Null** om strängen är null-terminerad.</span><span class="sxs-lookup"><span data-stu-id="eea0d-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-920">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-920">Return Values</span></span>

- <span data-ttu-id="eea0d-921">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-922">**NX_LWM2M_CLIENT_BAD_ENCODING** Resursens värde är inte ett sträng värde.</span><span class="sxs-lookup"><span data-stu-id="eea0d-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="eea0d-923">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-924">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-924">Allowed From</span></span>

<span data-ttu-id="eea0d-925">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-926">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="eea0d-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="eea0d-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="eea0d-928">Anger värdet för en sträng resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-929">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="eea0d-930">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-930">Description</span></span>

<span data-ttu-id="eea0d-931">Tjänsten anger värdet för en 64-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-932">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-932">Parameters</span></span>

- <span data-ttu-id="eea0d-933">**resurs** Pekare till resurs.</span><span class="sxs-lookup"><span data-stu-id="eea0d-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="eea0d-934">**string_ptr** Pekare till strängen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="eea0d-935">**string_length** Strängens längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-936">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-936">Return Values</span></span>

- <span data-ttu-id="eea0d-937">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-938">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-939">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-939">Allowed From</span></span>

<span data-ttu-id="eea0d-940">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-941">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="eea0d-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="eea0d-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="eea0d-943">Startar en-session med en Start Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-944">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="eea0d-945">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-945">Description</span></span>

<span data-ttu-id="eea0d-946">Den här tjänsten startar en session med en Start Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="eea0d-947">Servern måste ha en motsvarande säkerhets instans i objektet Security.</span><span class="sxs-lookup"><span data-stu-id="eea0d-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="eea0d-948">Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="eea0d-949">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-950">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-950">Parameters</span></span>

- <span data-ttu-id="eea0d-951">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="eea0d-952">**security_id** Start serverns säkerhets instans-ID måste anges till NX_LWM2M_RESERVED_ID (65535) om ingen säkerhets instans har definierats för bootstrap-servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="eea0d-953">**ip_address** Serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="eea0d-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="eea0d-954">**port** Serverns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="eea0d-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-955">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-955">Return Values</span></span>

- <span data-ttu-id="eea0d-956">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-957">**NX_LWM2M_CLIENT_ERROR** Start fel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="eea0d-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="eea0d-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="eea0d-959">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-960">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-960">Allowed From</span></span>

<span data-ttu-id="eea0d-961">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-962">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="eea0d-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="eea0d-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="eea0d-964">Startar en säker session med en Start Server</span><span class="sxs-lookup"><span data-stu-id="eea0d-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-965">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-966">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-966">Description</span></span>

<span data-ttu-id="eea0d-967">Den här tjänsten startar en session med en Start Server med en säker DTLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="eea0d-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="eea0d-968">Servern måste ha en motsvarande säkerhets instans i objektet Security.</span><span class="sxs-lookup"><span data-stu-id="eea0d-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="eea0d-969">DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="eea0d-970">**NX_SECURE_ENABLE_DTLS** måste definieras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="eea0d-971">Om resursen "vänta bort" skiljer sig från noll i säkerhets instansen som är kopplad till den här servern väntar sessionen på en initierad start av servern, om ingen start initieras av servern efter den här tids perioden som en klient initierade boostrap kommer att utföras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="eea0d-972">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya bootstrap-serversessionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-973">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-973">Parameters</span></span>

- <span data-ttu-id="eea0d-974">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="eea0d-975">**security_id** Start serverns säkerhets instans-ID måste anges till **NX_LWM2M_RESERVED_ID** (65535) om ingen säkerhets instans har definierats för bootstrap-servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="eea0d-976">**ip_address** Serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="eea0d-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="eea0d-977">**port** Serverns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="eea0d-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="eea0d-978">**dtls_session_ptr** DTLS-sessionen som ska användas för bootstrap-sessionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="eea0d-979">**dtls_local_port** Den lokala UDP-porten som används för DTLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-980">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-980">Return Values</span></span>

- <span data-ttu-id="eea0d-981">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-982">**NX_LWM2M_CLIENT_ERROR** Start fel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="eea0d-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="eea0d-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="eea0d-984">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-985">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-985">Allowed From</span></span>

<span data-ttu-id="eea0d-986">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-987">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="eea0d-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="eea0d-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="eea0d-989">Skapar en LWM2M-klientsession.</span><span class="sxs-lookup"><span data-stu-id="eea0d-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-990">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="eea0d-991">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-991">Description</span></span>

<span data-ttu-id="eea0d-992">Den här tjänsten skapar en ny LWM2M-klientsession som är ansluten till en befintlig LWM2M-klient.</span><span class="sxs-lookup"><span data-stu-id="eea0d-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="eea0d-993">Sessionen används av LWM2M-klienten för att kommunicera med en Start Server eller en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="eea0d-994">Programmet måste tillhandahålla en callback-funktion som anropas när sessionens tillstånd uppdateras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-995">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-995">Parameters</span></span>

- <span data-ttu-id="eea0d-996">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="eea0d-997">**client_ptr** Pekare till den tidigare skapade LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="eea0d-998">**state_callback** Återanrop från program som anropas när sessionens tillstånd har ändrats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-999">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-999">Return Values</span></span>

- <span data-ttu-id="eea0d-1000">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1001">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1002">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1002">Allowed From</span></span>

<span data-ttu-id="eea0d-1003">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1004">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="eea0d-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="eea0d-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="eea0d-1006">Tar bort en LWM2M-klientsession.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1007">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-1008">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1008">Description</span></span>

<span data-ttu-id="eea0d-1009">Den här tjänsten tar bort en LWM2M-klientsession.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="eea0d-1010">När en LWM2M-klient tas bort genom att anropa nx_lwm2m_client_delete alla sessioner som är anslutna till klienten också bort.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1011">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1011">Parameters</span></span>

- <span data-ttu-id="eea0d-1012">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1013">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1013">Return Values</span></span>

- <span data-ttu-id="eea0d-1014">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1015">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1016">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1016">Allowed From</span></span>

<span data-ttu-id="eea0d-1017">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1018">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="eea0d-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="eea0d-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="eea0d-1020">Avslutar en session med en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1021">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-1022">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1022">Description</span></span>

<span data-ttu-id="eea0d-1023">Den här tjänsten utför en "avregistrera"-åtgärd på en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1024">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1024">Parameters</span></span>

- <span data-ttu-id="eea0d-1025">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1026">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1026">Return Values</span></span>

- <span data-ttu-id="eea0d-1027">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** Klienten är inte registrerad på servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="eea0d-1029">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1030">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1030">Allowed From</span></span>

<span data-ttu-id="eea0d-1031">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1032">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="eea0d-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="eea0d-1034">Hämtar det senaste felet i en session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1035">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-1036">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1036">Description</span></span>

<span data-ttu-id="eea0d-1037">Den här tjänsten returnerar felkoden för sessionen när sessionen är i ett fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1038">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1038">Parameters</span></span>

- <span data-ttu-id="eea0d-1039">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1040">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1040">Return Values</span></span>

- <span data-ttu-id="eea0d-1041">**NX_SUCCESS** Sessionen är inte i ett fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="eea0d-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Ogiltig server adress.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="eea0d-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Nytto lasten för begäran får inte plats i nätverksmappen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="eea0d-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Det gick inte att upprätta en säker anslutning till servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="eea0d-1045">**NX_LWM2M_ CLIENT_ERROR** Okänt fel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="eea0d-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registreringen nekades av servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="eea0d-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Klienten kunde inte hittas av servern vid uppdatering/avregistrering.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="eea0d-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Server objekts instansen som motsvarar sessionen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="eea0d-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** Inget svar från servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="eea0d-1050">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1051">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1051">Allowed From</span></span>

<span data-ttu-id="eea0d-1052">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1053">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="eea0d-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="eea0d-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="eea0d-1055">Startar en session med en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1056">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="eea0d-1057">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1057">Description</span></span>

<span data-ttu-id="eea0d-1058">Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="eea0d-1059">Servern måste ha en motsvarande Server instans i objektet Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="eea0d-1060">Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="eea0d-1061">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1062">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1062">Parameters</span></span>

- <span data-ttu-id="eea0d-1063">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="eea0d-1064">**server_id** Det korta Server-ID: t för LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="eea0d-1065">**ip_address** Serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="eea0d-1066">**port** Serverns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1067">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1067">Return Values</span></span>

- <span data-ttu-id="eea0d-1068">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1069">**NX_LWM2M_CLIENT_ERROR** Start fel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="eea0d-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="eea0d-1071">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1072">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1072">Allowed From</span></span>

<span data-ttu-id="eea0d-1073">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1074">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="eea0d-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="eea0d-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="eea0d-1076">Startar en säker session med en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1077">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-1078">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1078">Description</span></span>

<span data-ttu-id="eea0d-1079">Den här tjänsten utför en "Registrera"-åtgärd på en LWM2M-server med en säker DTLS-anslutning.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="eea0d-1080">Servern måste ha en motsvarande Server instans i objektet Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="eea0d-1081">DTLS-sessionen måste ha kon figurer ATS med lämpliga chiffersviter och nyckel material innan du anropar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="eea0d-1082">**NX_SECURE_ENABLE_DTLS** måste definieras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="eea0d-1083">Om registreringen lyckas kommer LWM2M-klienten att bearbeta ytterligare åtgärder från servern och skickar regelbundet meddelanden om uppdatering tills klienten avregistreras.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="eea0d-1084">Alla pågående aktiva sessioner avbryts av det här anropet och ersätts av den nya LWM2M.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1085">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1085">Parameters</span></span>

- <span data-ttu-id="eea0d-1086">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="eea0d-1087">**server_id** Det korta Server-ID: t för LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="eea0d-1088">**ip_address** Serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="eea0d-1089">**port** Serverns UDP-port.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="eea0d-1090">**dtls_session_ptr** DTLS-sessionen som ska användas för LWM2M-sessionen.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1091">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1091">Return Values</span></span>

- <span data-ttu-id="eea0d-1092">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1093">**NX_LWM2M_CLIENT_ERROR** Start fel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="eea0d-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Porten är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="eea0d-1095">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1096">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1096">Allowed From</span></span>

<span data-ttu-id="eea0d-1097">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1098">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="eea0d-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="eea0d-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="eea0d-1100">Startar en säker session med en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1101">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="eea0d-1102">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1102">Description</span></span>

<span data-ttu-id="eea0d-1103">När en kommunikations-session med en Start Server upprättats.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="eea0d-1104">Programmet kan anropa detta API för att hämta server-och säkerhets information för nästa registrerings steg.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1105">Parameters</span></span>

- <span data-ttu-id="eea0d-1106">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="eea0d-1107">**security_instance_id** Säkerhets instans-ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="eea0d-1108">**server_id** Pekare till mål serverns ID.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="eea0d-1109">**server_uri** Pekare till mål serverns URI.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="eea0d-1110">**server_uri_len** Pekare till mål serverns URI-längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="eea0d-1111">**security_mode** Pekare till mål säkerhets läge.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="eea0d-1112">**pub_key_or_id** Pekare till den offentliga nyckeln eller identiteten.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="eea0d-1113">**pub_key_or_id_len** Pekare till målets offentliga nyckel eller identitets längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="eea0d-1114">**server_pub_key** Pekare till den offentliga nyckeln för mål servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="eea0d-1115">**server_pub_key_len** Pekare till mål serverns offentliga nyckel längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="eea0d-1116">**SECRET_KEY** Pekare till målets hemliga nyckel.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="eea0d-1117">**secret_key_len** Pekare till målets hemliga nyckel längd.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1118">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1118">Return Values</span></span>

- <span data-ttu-id="eea0d-1119">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1120">**NX_LWM2M_CLIENT_NOT_FOUND** Det finns ingen säkerhets objekts instans.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="eea0d-1121">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1122">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1122">Allowed From</span></span>

<span data-ttu-id="eea0d-1123">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1124">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="eea0d-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="eea0d-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="eea0d-1126">Uppdaterar en session med en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1127">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-1128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1128">Description</span></span>

<span data-ttu-id="eea0d-1129">Den här tjänsten utför en uppdaterings åtgärd på en LWM2M-Server.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1130">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1130">Parameters</span></span>

- <span data-ttu-id="eea0d-1131">**session_ptr** Pekare till LWM2M för klientens session.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1132">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1132">Return Values</span></span>

- <span data-ttu-id="eea0d-1133">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** Klienten är inte registrerad på servern.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="eea0d-1135">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1136">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1136">Allowed From</span></span>

<span data-ttu-id="eea0d-1137">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1138">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="eea0d-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="eea0d-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="eea0d-1140">Låser upp en LWM2M-klient.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="eea0d-1141">Prototyp</span><span class="sxs-lookup"><span data-stu-id="eea0d-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="eea0d-1142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eea0d-1142">Description</span></span>

<span data-ttu-id="eea0d-1143">Den här tjänsten låser upp LWM2M-klienten som tidigare låstes av ett anrop till ***nx_lwm2m_client_unlock***.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="eea0d-1144">Parametrar</span><span class="sxs-lookup"><span data-stu-id="eea0d-1144">Parameters</span></span>

- <span data-ttu-id="eea0d-1145">**client_ptr** Pekare till LWM2M klient kontroll block.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="eea0d-1146">Retur värden</span><span class="sxs-lookup"><span data-stu-id="eea0d-1146">Return Values</span></span>

- <span data-ttu-id="eea0d-1147">**NX_SUCCESS** Åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="eea0d-1148">**NX_PTR_ERROR** Ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="eea0d-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="eea0d-1149">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="eea0d-1149">Allowed From</span></span>

<span data-ttu-id="eea0d-1150">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="eea0d-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="eea0d-1151">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea0d-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```