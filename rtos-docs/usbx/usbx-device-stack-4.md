---
title: Kapitel 4 – Beskrivning av USBX Device Services
description: Läs mer om USBX Device Services.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828137"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="adda0-103">Beskrivning av USBX Device Services</span><span class="sxs-lookup"><span data-stu-id="adda0-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="adda0-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="adda0-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="adda0-105">Hämta aktuell alternativ inställning för ett gränssnitts värde</span><span class="sxs-lookup"><span data-stu-id="adda0-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="adda0-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-107">Description</span></span>

<span data-ttu-id="adda0-108">Den här funktionen används av USB-värden för att hämta den aktuella alternativa inställningen för ett angivet gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="adda0-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="adda0-109">Den anropas av styrenhetens driv rutin när en **GET_INTERFACE** -begäran tas emot.</span><span class="sxs-lookup"><span data-stu-id="adda0-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-110">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-110">Input Parameter</span></span>

- <span data-ttu-id="adda0-111">**Interface_value** Gränssnitts värde som den aktuella alternativa inställningen efterfrågar</span><span class="sxs-lookup"><span data-stu-id="adda0-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-112">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-112">Return Values</span></span>

- <span data-ttu-id="adda0-113">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="adda0-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="adda0-114">**UX_ERROR** (0Xff) felaktigt gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="adda0-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="adda0-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="adda0-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="adda0-117">Ange den aktuella alternativa inställningen för ett gränssnitts värde</span><span class="sxs-lookup"><span data-stu-id="adda0-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-118">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="adda0-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-119">Description</span></span>

<span data-ttu-id="adda0-120">Den här funktionen används av USB-värden för att ange den aktuella alternativa inställningen för ett angivet gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="adda0-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="adda0-121">Den anropas av styrenhetens driv rutin när en **SET_INTERFACE** -begäran tas emot.</span><span class="sxs-lookup"><span data-stu-id="adda0-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="adda0-122">När **SET_INTERFACE** har slutförts används värdena för de alternativa inställningarna i klassen.</span><span class="sxs-lookup"><span data-stu-id="adda0-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="adda0-123">Enhets stacken utfärdar en **UX_SLAVE_CLASS_COMMAND_CHANGE** till den klass som äger det här gränssnittet för att återspegla ändringen av en alternativ inställning.</span><span class="sxs-lookup"><span data-stu-id="adda0-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-124">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-124">Parameters</span></span>

- <span data-ttu-id="adda0-125">**interface_value**: gränssnitts värde som den aktuella alternativa inställningen har angetts för.</span><span class="sxs-lookup"><span data-stu-id="adda0-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="adda0-126">**alternate_setting_value**: det nya värdet för alternativ inställning.</span><span class="sxs-lookup"><span data-stu-id="adda0-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-127">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-127">Return Values</span></span>

- <span data-ttu-id="adda0-128">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="adda0-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="adda0-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0X52) inget gränssnitt har bifogats.</span><span class="sxs-lookup"><span data-stu-id="adda0-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="adda0-130">**UX_FUNCTION_NOT_SUPPORTED** -enheten (0x54) har inte kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="adda0-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="adda0-131">**UX_ERROR** (0Xff) felaktigt gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="adda0-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="adda0-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="adda0-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="adda0-134">Registrera en ny USB-enhets klass</span><span class="sxs-lookup"><span data-stu-id="adda0-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-135">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="adda0-136">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-136">Description</span></span>

<span data-ttu-id="adda0-137">Den här funktionen används av programmet för att registrera en ny USB-enhets klass.</span><span class="sxs-lookup"><span data-stu-id="adda0-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="adda0-138">Den här registreringen startar en klass behållare och inte en instans av klassen.</span><span class="sxs-lookup"><span data-stu-id="adda0-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="adda0-139">En klass måste ha en aktiv tråd och vara kopplad till ett särskilt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="adda0-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="adda0-140">Vissa klasser förväntar sig en parameter-eller parameter lista.</span><span class="sxs-lookup"><span data-stu-id="adda0-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="adda0-141">Enhets lagrings klassen förväntar sig till exempel geometrin för lagrings enheten som den försöker emulera.</span><span class="sxs-lookup"><span data-stu-id="adda0-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="adda0-142">Parameter fältet är därför beroende av klass kravet och kan vara ett värde eller en pekare till en struktur som är ifylld med klass värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="adda0-143">C-strängen för class_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="adda0-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-144">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-144">Parameters</span></span>

- <span data-ttu-id="adda0-145">**class_name** Klass namn</span><span class="sxs-lookup"><span data-stu-id="adda0-145">**class_name** Class Name</span></span>
- <span data-ttu-id="adda0-146">**class_entry_function** Funktionen post i klassen.</span><span class="sxs-lookup"><span data-stu-id="adda0-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="adda0-147">**configuration_number** Konfigurations numret som den här klassen är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="adda0-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="adda0-148">**interface_number** Gränssnitts numret som den här klassen är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="adda0-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="adda0-149">**parameter** En pekare till en lista med landsspecifika parametrar.</span><span class="sxs-lookup"><span data-stu-id="adda0-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-150">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-150">Return Values</span></span>

- <span data-ttu-id="adda0-151">**UX_SUCCESS** (0x00) klassen har registrerats</span><span class="sxs-lookup"><span data-stu-id="adda0-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="adda0-152">**UX_MEMORY_INSUFFICIENT** (0X12) inga poster kvar i klass tabellen.</span><span class="sxs-lookup"><span data-stu-id="adda0-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="adda0-153">**UX_THREAD_ERROR** (0X16) kan inte skapa en klass tråd.</span><span class="sxs-lookup"><span data-stu-id="adda0-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="adda0-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="adda0-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="adda0-156">Avregistrera en USB-enhets klass</span><span class="sxs-lookup"><span data-stu-id="adda0-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-157">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="adda0-158">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-158">Description</span></span>

<span data-ttu-id="adda0-159">Den här funktionen används av programmet för att avregistrera en USB-enhets klass.</span><span class="sxs-lookup"><span data-stu-id="adda0-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="adda0-160">C-strängen för class_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="adda0-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-161">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-161">Parameters</span></span>

- <span data-ttu-id="adda0-162">**class_name**: klass namn</span><span class="sxs-lookup"><span data-stu-id="adda0-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="adda0-163">**class_entry_function**: post funktionen i klassen.</span><span class="sxs-lookup"><span data-stu-id="adda0-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-164">Return Values</span></span>

- <span data-ttu-id="adda0-165">**UX_SUCCESS** (0x00) klassen har avregistrerats.</span><span class="sxs-lookup"><span data-stu-id="adda0-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="adda0-166">**UX_NO_CLASS_MATCH** (0x57) klassen är inte registrerad.</span><span class="sxs-lookup"><span data-stu-id="adda0-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-167">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="adda0-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="adda0-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="adda0-169">Hämta den aktuella konfigurationen</span><span class="sxs-lookup"><span data-stu-id="adda0-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-170">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="adda0-171">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-171">Description</span></span>

<span data-ttu-id="adda0-172">Den här funktionen används av värden för att hämta den aktuella konfigurationen som körs i enheten.</span><span class="sxs-lookup"><span data-stu-id="adda0-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-173">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-173">Input Parameter</span></span>

<span data-ttu-id="adda0-174">Inget</span><span class="sxs-lookup"><span data-stu-id="adda0-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-175">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-175">Return Value</span></span>

- <span data-ttu-id="adda0-176">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="adda0-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-177">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="adda0-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="adda0-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="adda0-179">Ange den aktuella konfigurationen</span><span class="sxs-lookup"><span data-stu-id="adda0-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-180">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="adda0-181">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-181">Description</span></span>

<span data-ttu-id="adda0-182">Den här funktionen används av värden för att ange den aktuella konfigurationen som körs i enheten.</span><span class="sxs-lookup"><span data-stu-id="adda0-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="adda0-183">Vid mottagande av det här kommandot aktiverar USB-enheten den alternativa inställningen 0 för varje gränssnitt som är anslutet till den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="adda0-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-184">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-184">Input Parameter</span></span>

- <span data-ttu-id="adda0-185">**configuration_value** Konfiguration svärdet som valts av värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-186">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-186">Return Value</span></span>

- <span data-ttu-id="adda0-187">**UX_SUCCESS** (0x00) konfigurationen har angetts.</span><span class="sxs-lookup"><span data-stu-id="adda0-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-188">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="adda0-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="adda0-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="adda0-190">Skicka en beskrivning till värden</span><span class="sxs-lookup"><span data-stu-id="adda0-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-191">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="adda0-192">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-192">Description</span></span>

<span data-ttu-id="adda0-193">Den här funktionen används av enhets sidan för att returnera en beskrivning till värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="adda0-194">Den här beskrivningen kan vara en enhets beskrivning, en konfigurations beskrivning eller en sträng beskrivning.</span><span class="sxs-lookup"><span data-stu-id="adda0-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-195">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-195">Parameters</span></span>

- <span data-ttu-id="adda0-196">**descriptor_type**: typ av beskrivning.</span><span class="sxs-lookup"><span data-stu-id="adda0-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="adda0-197">Måste vara något av följande värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="adda0-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="adda0-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="adda0-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="adda0-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="adda0-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="adda0-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="adda0-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="adda0-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="adda0-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="adda0-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="adda0-203">**request_index**: indexet för beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="adda0-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="adda0-204">**host_length**: längden som krävs av värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-205">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-205">Return Values</span></span>

- <span data-ttu-id="adda0-206">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="adda0-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="adda0-207">**UX_ERROR** (0xFF) överföringen slutfördes inte.</span><span class="sxs-lookup"><span data-stu-id="adda0-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-208">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="adda0-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="adda0-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="adda0-210">Koppla bort enhets stack</span><span class="sxs-lookup"><span data-stu-id="adda0-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-211">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="adda0-212">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-212">Description</span></span>

<span data-ttu-id="adda0-213">VBUS Manager anropar den här funktionen när det finns en enhets anslutning.</span><span class="sxs-lookup"><span data-stu-id="adda0-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="adda0-214">Enhets stacken meddelar alla klasser som är registrerade för enheten och släpper därefter alla enhets resurser.</span><span class="sxs-lookup"><span data-stu-id="adda0-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-215">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-215">Input Parameter</span></span>

<span data-ttu-id="adda0-216">Inget</span><span class="sxs-lookup"><span data-stu-id="adda0-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-217">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-217">Return Value</span></span>

- <span data-ttu-id="adda0-218">**UX_SUCCESS** (0x00) enheten kopplades från.</span><span class="sxs-lookup"><span data-stu-id="adda0-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-219">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="adda0-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="adda0-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="adda0-221">Villkor för begär slut punkts ficka</span><span class="sxs-lookup"><span data-stu-id="adda0-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-222">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="adda0-223">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-223">Description</span></span>

<span data-ttu-id="adda0-224">Den här funktionen anropas av USB-enhetens klass när en slut punkt ska returnera ett ficka-villkor till värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-225">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-225">Input Parameter</span></span>

- <span data-ttu-id="adda0-226">**slut punkt** Den slut punkt där parkerings villkoret har begärts.</span><span class="sxs-lookup"><span data-stu-id="adda0-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-227">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-227">Return Value</span></span>

- <span data-ttu-id="adda0-228">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="adda0-229">**UX_ERROR** (0xFF) enheten är i ett ogiltigt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="adda0-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-230">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="adda0-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="adda0-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="adda0-232">Väcka värden</span><span class="sxs-lookup"><span data-stu-id="adda0-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-233">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="adda0-234">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-234">Description</span></span>

<span data-ttu-id="adda0-235">Den här funktionen anropas när enheten vill aktivera värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="adda0-236">Det här kommandot är endast giltigt när enheten är i paus läge.</span><span class="sxs-lookup"><span data-stu-id="adda0-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="adda0-237">Det är upp till enhets programmet som avgör när du vill aktivera USB-värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="adda0-238">Ett USB-modem kan till exempel aktivera en värd när den identifierar en RING signal på telefon linjen.</span><span class="sxs-lookup"><span data-stu-id="adda0-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-239">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-239">Input Parameter</span></span>

<span data-ttu-id="adda0-240">Inget</span><span class="sxs-lookup"><span data-stu-id="adda0-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-241">Returvärden</span><span class="sxs-lookup"><span data-stu-id="adda0-241">Return values</span></span>

- <span data-ttu-id="adda0-242">**UX_SUCCESS** (0x00) anropet lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="adda0-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) anropet misslyckades (enheten var förmodligen inte i paus läge).</span><span class="sxs-lookup"><span data-stu-id="adda0-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="adda0-244">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="adda0-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="adda0-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="adda0-246">Initiera USB-enhets stack</span><span class="sxs-lookup"><span data-stu-id="adda0-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-247">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="adda0-248">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-248">Description</span></span>

<span data-ttu-id="adda0-249">Den här funktionen anropas av programmet för att initiera USB-enhetens stack.</span><span class="sxs-lookup"><span data-stu-id="adda0-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="adda0-250">De initierar inga klasser eller styrenheter.</span><span class="sxs-lookup"><span data-stu-id="adda0-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="adda0-251">Detta bör göras med separata funktions anrop.</span><span class="sxs-lookup"><span data-stu-id="adda0-251">This should be done with separate function calls.</span></span> <span data-ttu-id="adda0-252">Det här anropet tillhandahåller huvudsakligen stacken med enhets ramverket för USB-funktionen.</span><span class="sxs-lookup"><span data-stu-id="adda0-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="adda0-253">Det stöder både hög och fullständig hastighet med möjligheten att ha helt separata enhets ramverk för varje hastighet.</span><span class="sxs-lookup"><span data-stu-id="adda0-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="adda0-254">Sträng ramverk och flera språk stöds.</span><span class="sxs-lookup"><span data-stu-id="adda0-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-255">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-255">Parameters</span></span>

- <span data-ttu-id="adda0-256">**device_framework_high_speed**: pekar mot ramverket med hög hastighet.</span><span class="sxs-lookup"><span data-stu-id="adda0-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="adda0-257">**device_framework_length_high_speed**: längden på ramverket med hög hastighet.</span><span class="sxs-lookup"><span data-stu-id="adda0-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="adda0-258">**device_framework_full_speed**: pekar mot ramverket med full hastighet.</span><span class="sxs-lookup"><span data-stu-id="adda0-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="adda0-259">**device_framework_length_full_speed**: längden på ramverket med full hastighet.</span><span class="sxs-lookup"><span data-stu-id="adda0-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="adda0-260">**string_framework**: pekar mot sträng ramverk.</span><span class="sxs-lookup"><span data-stu-id="adda0-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="adda0-261">**string_framework_length**: sträng ramverkets längd.</span><span class="sxs-lookup"><span data-stu-id="adda0-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="adda0-262">**language_id_framework**: pekar mot sträng språks ramverk.</span><span class="sxs-lookup"><span data-stu-id="adda0-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="adda0-263">**language_id_framework_length**: längden på sträng språk ramverket.</span><span class="sxs-lookup"><span data-stu-id="adda0-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="adda0-264">**ux_system_slave_change_function**: funktion som ska anropas när enhetens tillstånd ändras.</span><span class="sxs-lookup"><span data-stu-id="adda0-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-265">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-265">Return Values</span></span>

- <span data-ttu-id="adda0-266">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="adda0-267">**UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för att initiera stacken.</span><span class="sxs-lookup"><span data-stu-id="adda0-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="adda0-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) beskrivningen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="adda0-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-269">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="adda0-270">Programmet kan begära ett anrop igen när styrenheten ändrar sitt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="adda0-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="adda0-271">De två huvud tillstånden för kontrollanten är:</span><span class="sxs-lookup"><span data-stu-id="adda0-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="adda0-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="adda0-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="adda0-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="adda0-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="adda0-274">Om programmet inte behöver pausa/återuppta signaler, skulle det tillhandahålla en UX_NULL-funktion.</span><span class="sxs-lookup"><span data-stu-id="adda0-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="adda0-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="adda0-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="adda0-276">Ta bort ett stack gränssnitt</span><span class="sxs-lookup"><span data-stu-id="adda0-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-277">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="adda0-278">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-278">Description</span></span>

<span data-ttu-id="adda0-279">Den här funktionen anropas när ett gränssnitt ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="adda0-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="adda0-280">Ett gränssnitt tas bort när en enhet extraheras eller följer en återställning av bussen eller när det finns en ny alternativ inställning.</span><span class="sxs-lookup"><span data-stu-id="adda0-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-281">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-281">Input Parameter</span></span>

- <span data-ttu-id="adda0-282">**gränssnitt**: pekar på det gränssnitt som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="adda0-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-283">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-283">Return Value</span></span>

- <span data-ttu-id="adda0-284">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-285">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="adda0-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="adda0-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="adda0-287">Hämta det aktuella gränssnitt svärdet</span><span class="sxs-lookup"><span data-stu-id="adda0-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-288">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="adda0-289">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-289">Description</span></span>

<span data-ttu-id="adda0-290">Den här funktionen anropas när värden frågar det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="adda0-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="adda0-291">Enheten returnerar det aktuella gränssnitt svärdet.</span><span class="sxs-lookup"><span data-stu-id="adda0-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="adda0-292">Den här funktionen är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="adda0-292">This function is deprecated.</span></span> <span data-ttu-id="adda0-293">Den är tillgänglig för äldre program vara, men den nya program varan bör använda funktionen ***ux_device_stack_alternate_setting_get*** i stället.</span><span class="sxs-lookup"><span data-stu-id="adda0-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-294">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-294">Input Parameter</span></span>

- <span data-ttu-id="adda0-295">**interface_value** Gränssnitts värde att returnera.</span><span class="sxs-lookup"><span data-stu-id="adda0-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-296">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-296">Return Values</span></span>

- <span data-ttu-id="adda0-297">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="adda0-298">**UX_ERROR** (0Xff) inget gränssnitt finns.</span><span class="sxs-lookup"><span data-stu-id="adda0-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-299">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="adda0-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="adda0-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="adda0-301">Ändra gränssnittets alternativa inställning</span><span class="sxs-lookup"><span data-stu-id="adda0-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-302">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="adda0-303">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-303">Description</span></span>

<span data-ttu-id="adda0-304">Den här funktionen anropas när värden begär en ändring av den alternativa inställningen för gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="adda0-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-305">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-305">Parameters</span></span>

- <span data-ttu-id="adda0-306">**device_framework**: adressen för det här gränssnittets enhets ramverk.</span><span class="sxs-lookup"><span data-stu-id="adda0-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="adda0-307">**device_framework_length**: enhets ramverkets längd.</span><span class="sxs-lookup"><span data-stu-id="adda0-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="adda0-308">**alternate_setting_value**: alternativ inställnings värde som ska användas av det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="adda0-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-309">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-309">Return Values</span></span>

- <span data-ttu-id="adda0-310">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="adda0-311">**UX_ERROR** (0Xff) inget gränssnitt finns.</span><span class="sxs-lookup"><span data-stu-id="adda0-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-312">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="adda0-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="adda0-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="adda0-314">Starta sökning efter en klass för att äga en gränssnitts instans</span><span class="sxs-lookup"><span data-stu-id="adda0-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-315">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="adda0-316">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-316">Description</span></span>

<span data-ttu-id="adda0-317">Den här funktionen anropas när ett gränssnitt har valts av värden och enhets stacken måste söka efter en enhets klass för att äga den här gränssnitts instansen.</span><span class="sxs-lookup"><span data-stu-id="adda0-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="adda0-318">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="adda0-318">Input Parameter</span></span>

- <span data-ttu-id="adda0-319">**gränssnitt**: pekar mot gränssnittet som skapats.</span><span class="sxs-lookup"><span data-stu-id="adda0-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-320">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-320">Return Values</span></span>

- <span data-ttu-id="adda0-321">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="adda0-322">**UX_NO_CLASS_MATCH** (0x57) det finns ingen klass för det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="adda0-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-323">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="adda0-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="adda0-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="adda0-325">Begäran om att överföra data till värden</span><span class="sxs-lookup"><span data-stu-id="adda0-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-326">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="adda0-327">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-327">Description</span></span>

<span data-ttu-id="adda0-328">Den här funktionen anropas när en klass eller stacken vill överföra data till värden.</span><span class="sxs-lookup"><span data-stu-id="adda0-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="adda0-329">Värden avsöker alltid enheten men enheten kan förbereda data i förväg.</span><span class="sxs-lookup"><span data-stu-id="adda0-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-330">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-330">Parameters</span></span>

- <span data-ttu-id="adda0-331">**transfer_request**: pekar mot överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="adda0-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="adda0-332">**slave_length**: den längd som enheten vill returnera.</span><span class="sxs-lookup"><span data-stu-id="adda0-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="adda0-333">**host_length**: längden på värden har begärts.</span><span class="sxs-lookup"><span data-stu-id="adda0-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="adda0-334">Retur värden</span><span class="sxs-lookup"><span data-stu-id="adda0-334">Return Values</span></span>

- <span data-ttu-id="adda0-335">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="adda0-336">**UX_TRANSFER_NOT_READY** (0x25) enheten är i ett ogiltigt tillstånd. den måste vara **ansluten**, **konfigurerad** eller **adresserad**.</span><span class="sxs-lookup"><span data-stu-id="adda0-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="adda0-337">**UX_ERROR** (0Xff) transport fel.</span><span class="sxs-lookup"><span data-stu-id="adda0-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-338">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="adda0-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="adda0-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="adda0-340">Avbryta en överföringsbegäran</span><span class="sxs-lookup"><span data-stu-id="adda0-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-341">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="adda0-342">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-342">Description</span></span>

<span data-ttu-id="adda0-343">Den här funktionen anropas när ett program måste avbryta en överförings förfrågan eller när stacken måste avbryta en överföringsbegäran som är associerad med en slut punkt.</span><span class="sxs-lookup"><span data-stu-id="adda0-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-344">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-344">Parameters</span></span>

- <span data-ttu-id="adda0-345">**transfer_request**: pekar mot överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="adda0-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="adda0-346">**completion_code**: den felkod som ska returneras till klassen som väntar på att denna överföringsbegäran ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="adda0-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-347">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-347">Return Value</span></span>

- <span data-ttu-id="adda0-348">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="adda0-349">Exempel</span><span class="sxs-lookup"><span data-stu-id="adda0-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="adda0-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="adda0-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="adda0-351">Unitialize-stack</span><span class="sxs-lookup"><span data-stu-id="adda0-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="adda0-352">Prototyp</span><span class="sxs-lookup"><span data-stu-id="adda0-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="adda0-353">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="adda0-353">Description</span></span>

<span data-ttu-id="adda0-354">Den här funktionen anropas när ett program behöver unitialize USBX Device-stacken – alla enhets stack resurser frigörs.</span><span class="sxs-lookup"><span data-stu-id="adda0-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="adda0-355">Detta ska anropas när alla klasser har avregistrerats via ux_device_stack_class_unregister.</span><span class="sxs-lookup"><span data-stu-id="adda0-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="adda0-356">Parametrar</span><span class="sxs-lookup"><span data-stu-id="adda0-356">Parameters</span></span>

<span data-ttu-id="adda0-357">Ingen</span><span class="sxs-lookup"><span data-stu-id="adda0-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="adda0-358">Returvärde</span><span class="sxs-lookup"><span data-stu-id="adda0-358">Return Value</span></span>

<span data-ttu-id="adda0-359">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="adda0-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
