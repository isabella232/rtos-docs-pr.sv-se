---
title: Kapitel 4 – Beskrivning av USBX-värd tjänster
description: Läs mer om USBX-värd tjänsterna.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828455"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="3dc47-103">Kapitel 4 – Beskrivning av USBX-värd tjänster</span><span class="sxs-lookup"><span data-stu-id="3dc47-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="3dc47-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="3dc47-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="3dc47-105">Initiera USBX för värd åtgärd.</span><span class="sxs-lookup"><span data-stu-id="3dc47-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="3dc47-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-107">Description</span></span>

<span data-ttu-id="3dc47-108">Den här funktionen initierar USB-värdstyrenheten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="3dc47-109">Det tillhandahållna minnes området kommer att konfigureras för intern användning av USBX.</span><span class="sxs-lookup"><span data-stu-id="3dc47-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="3dc47-110">Om UX_SUCCESS returneras är USBX redo för värd styrenhet och klass registrering.</span><span class="sxs-lookup"><span data-stu-id="3dc47-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3dc47-111">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="3dc47-111">Input Parameter</span></span>

- <span data-ttu-id="3dc47-112">**system_change_function** Pekare till valfri callback-rutin för att meddela program om enhets ändringar.</span><span class="sxs-lookup"><span data-stu-id="3dc47-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="3dc47-113">Returvärde</span><span class="sxs-lookup"><span data-stu-id="3dc47-113">Return Value</span></span>

- <span data-ttu-id="3dc47-114">**UX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="3dc47-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="3dc47-115">**UX_MEMORY_INSUFFICIENT** (0X12) en minnesallokering misslyckades.</span><span class="sxs-lookup"><span data-stu-id="3dc47-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="3dc47-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="3dc47-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="3dc47-118">Avbryt alla transaktioner som är kopplade till en överföringsbegäran för en slut punkt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-119">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="3dc47-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-120">Description</span></span>

<span data-ttu-id="3dc47-121">Den här funktionen avbryter alla transaktioner som är aktiva eller väntar på en angiven överföringsbegäran som är kopplad till en slut punkt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="3dc47-122">Den överförings förfrågan har en kopplad motringning, anropas funktionen motringning med UX_TRANSACTION_ABORTEDs status.</span><span class="sxs-lookup"><span data-stu-id="3dc47-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3dc47-123">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="3dc47-123">Input Parameter</span></span>

- <span data-ttu-id="3dc47-124">**slut punkt** Pekare till en slut punkt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-125">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-125">Return Values</span></span>

- <span data-ttu-id="3dc47-126">**UX_SUCCESS** (0X00) inga fel.</span><span class="sxs-lookup"><span data-stu-id="3dc47-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="3dc47-127">Slut punkts referensen för **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="3dc47-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="3dc47-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="3dc47-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="3dc47-130">Hämta pekaren till en klass behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-131">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="3dc47-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-132">Description</span></span>

<span data-ttu-id="3dc47-133">Den här funktionen returnerar en pekare till klass containern.</span><span class="sxs-lookup"><span data-stu-id="3dc47-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="3dc47-134">En klass behöver hämta sin behållare från USB-stacken för att söka efter instanser när en klass eller ett program vill öppna en enhet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="3dc47-135">C-strängen för class_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än UX_MAX_CLASS_NAME_LENGTH.</span><span class="sxs-lookup"><span data-stu-id="3dc47-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-136">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-136">Parameters</span></span>

- <span data-ttu-id="3dc47-137">**class_name** Pekar mot klass namnet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="3dc47-138">**klass** En pekare som uppdaterats av funktions anropet och som innehåller klass behållaren för namnet på klassen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-139">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-139">Return Values</span></span>

- <span data-ttu-id="3dc47-140">**UX_SUCCESS** (0X00) inga fel, i returnera klass fältet arkiveras med pekaren till klass behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="3dc47-141">**UX_HOST_CLASS_UNKNOWN** (0x59)-klassen är okänd i stacken.</span><span class="sxs-lookup"><span data-stu-id="3dc47-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-142">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="3dc47-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="3dc47-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="3dc47-144">Registrera en USB-klass på USB-stacken.</span><span class="sxs-lookup"><span data-stu-id="3dc47-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-145">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="3dc47-146">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-146">Description</span></span>

<span data-ttu-id="3dc47-147">Den här funktionen registrerar en USB-klass i USB-stacken.</span><span class="sxs-lookup"><span data-stu-id="3dc47-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="3dc47-148">Klassen måste ange en start punkt för USB-stacken för att skicka kommandon som följande.</span><span class="sxs-lookup"><span data-stu-id="3dc47-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="3dc47-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="3dc47-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="3dc47-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="3dc47-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="3dc47-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="3dc47-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="3dc47-152">C-strängen för *class_name* måste vara null-terminerad och längden på den (utan själva null-begränsaren) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="3dc47-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-153">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-153">Parameters</span></span>

- <span data-ttu-id="3dc47-154">**class_name** Pekar till namnet på klassen. giltiga poster finns i filen ux_system_initialize. c under USB-klasserna för USBX.</span><span class="sxs-lookup"><span data-stu-id="3dc47-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="3dc47-155">**class_entry_address** Adress till post-funktionen för klassen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-156">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-156">Return Values</span></span>

- <span data-ttu-id="3dc47-157">Klassen **UX_SUCCESS** (0x00) har installerats.</span><span class="sxs-lookup"><span data-stu-id="3dc47-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="3dc47-158">**UX_MEMORY_ARRAY_FULL** (0x1a) Det går inte att lagra den här klassen med mer minne.</span><span class="sxs-lookup"><span data-stu-id="3dc47-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="3dc47-159">Värd klassen för **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) är redan installerad.</span><span class="sxs-lookup"><span data-stu-id="3dc47-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-160">Exempel:</span><span class="sxs-lookup"><span data-stu-id="3dc47-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="3dc47-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="3dc47-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="3dc47-162">Skapa en ny klass instans för en klass behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-163">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="3dc47-164">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-164">Description</span></span>

<span data-ttu-id="3dc47-165">Den här funktionen skapar en ny klass instans för en klass behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="3dc47-166">Instansen för en klass ingår inte i klass koden för att minska klass komplexiteten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="3dc47-167">I stället är varje klass instans kopplad till klass behållaren som finns i huvud stacken.</span><span class="sxs-lookup"><span data-stu-id="3dc47-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-168">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-168">Parameters</span></span>

- <span data-ttu-id="3dc47-169">**klass** Pekare till klass behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="3dc47-170">**class_instance** Pekare till klass instansen som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="3dc47-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="3dc47-171">Returvärde</span><span class="sxs-lookup"><span data-stu-id="3dc47-171">Return Value</span></span>

- <span data-ttu-id="3dc47-172">**UX_SUCCESS** (0x00) klass instansen anslöts till klass containern.</span><span class="sxs-lookup"><span data-stu-id="3dc47-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-173">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="3dc47-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="3dc47-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="3dc47-175">Förstör en klass instans för en klass behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-176">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="3dc47-177">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-177">Description</span></span>

<span data-ttu-id="3dc47-178">Den här funktionen förstör en klass instans för en klass behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-179">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-179">Parameters</span></span>

- <span data-ttu-id="3dc47-180">**klass** Pekare till klass behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="3dc47-181">**class_instance** Pekar på den instans som ska förstöras.</span><span class="sxs-lookup"><span data-stu-id="3dc47-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-182">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-182">Return Values</span></span>

- <span data-ttu-id="3dc47-183">**UX_SUCCESS** (0x00) klass instansen har förstörts.</span><span class="sxs-lookup"><span data-stu-id="3dc47-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="3dc47-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) klass instansen är inte kopplad till klass containern.</span><span class="sxs-lookup"><span data-stu-id="3dc47-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-185">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="3dc47-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="3dc47-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="3dc47-187">Hämta en klass instans pekare för en speciell klass.</span><span class="sxs-lookup"><span data-stu-id="3dc47-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-188">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="3dc47-189">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-189">Description</span></span>

<span data-ttu-id="3dc47-190">Den här funktionen returnerar en klass instans pekare för en speciell klass.</span><span class="sxs-lookup"><span data-stu-id="3dc47-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="3dc47-191">Instansen för en klass ingår inte i klass koden för att minska klass komplexiteten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="3dc47-192">Varje klass instans är i stället kopplad till klass behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="3dc47-193">Den här funktionen används för att söka efter klass instanser i en klass behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-194">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-194">Parameters</span></span>

- <span data-ttu-id="3dc47-195">**klass** Pekare till klass behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="3dc47-196">**class_index** Ett index som ska användas av funktions anropet i listan över anslutna klasser till behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="3dc47-197">**class_instance** Pekare till den instans som ska returneras av funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-198">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-198">Return Values</span></span>

- <span data-ttu-id="3dc47-199">**UX_SUCCESS** (0x00) klass instansen påträffades.</span><span class="sxs-lookup"><span data-stu-id="3dc47-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="3dc47-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b) det finns inga fler klass instanser kopplade till klass behållaren.</span><span class="sxs-lookup"><span data-stu-id="3dc47-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-201">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="3dc47-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="3dc47-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="3dc47-203">Hämta en pekare till en konfigurations behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-204">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="3dc47-205">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-205">Description</span></span>

<span data-ttu-id="3dc47-206">Den här funktionen returnerar en konfigurations behållare baserat på en enhets referens och ett konfigurations index.</span><span class="sxs-lookup"><span data-stu-id="3dc47-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-207">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-207">Parameters</span></span>

- <span data-ttu-id="3dc47-208">**enhet** Pekar till enhets behållaren som äger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="3dc47-209">**configuration_index** Index för den konfiguration som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="3dc47-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="3dc47-210">**konfiguration** Adress till den-pekare till den konfigurations behållare som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="3dc47-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-211">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-211">Return Values</span></span>

- <span data-ttu-id="3dc47-212">**UX_SUCCESS** (0x00) konfigurationen hittades.</span><span class="sxs-lookup"><span data-stu-id="3dc47-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="3dc47-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) enhets containern finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="3dc47-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) konfigurations referensen för indexet finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-215">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="3dc47-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="3dc47-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="3dc47-217">Välj en speciell konfiguration för en enhet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-218">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="3dc47-219">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-219">Description</span></span>

<span data-ttu-id="3dc47-220">Den här funktionen väljer en speciell konfiguration för en enhet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="3dc47-221">När den här konfigurationen är inställd på enheten aktive ras som standard alla enhets gränssnitt och den tillhör ande alternativa inställningen 0 på enheten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="3dc47-222">Om enhets-och gränssnitts klassen vill ändra inställningen för ett visst gränssnitt måste den utfärda ett **ux_host_stack_interface_setting_select** tjänst anrop.</span><span class="sxs-lookup"><span data-stu-id="3dc47-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-223">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-223">Parameters</span></span>

- <span data-ttu-id="3dc47-224">**konfiguration** Pekar till den konfigurations behållare som ska aktive ras för den här enheten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-225">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-225">Return Values</span></span>

- <span data-ttu-id="3dc47-226">**UX_SUCCESS** (0x00) konfigurations valet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="3dc47-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="3dc47-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) konfigurations referensen finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="3dc47-228">**UX_OVER_CURRENT_CONDITION** (0X43) ett över aktuellt villkor finns på bussen för den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-229">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="3dc47-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="3dc47-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="3dc47-231">Hämta en pekare till en enhets behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-232">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="3dc47-233">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-233">Description</span></span>

<span data-ttu-id="3dc47-234">Den här funktionen returnerar en enhets behållare baserat på dess index.</span><span class="sxs-lookup"><span data-stu-id="3dc47-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="3dc47-235">Enhets indexet börjar med 0.</span><span class="sxs-lookup"><span data-stu-id="3dc47-235">The device index starts with 0.</span></span> <span data-ttu-id="3dc47-236">Observera att indexet är en ULONG eftersom vi kan ha flera styrenheter och ett byte-index kanske inte räcker till.</span><span class="sxs-lookup"><span data-stu-id="3dc47-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="3dc47-237">Enhets indexet ska inte förväxlas med den enhets adress som är buss-/regionsspecifika.</span><span class="sxs-lookup"><span data-stu-id="3dc47-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-238">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-238">Parameters</span></span>

- <span data-ttu-id="3dc47-239">**device_index** Enhetens index.</span><span class="sxs-lookup"><span data-stu-id="3dc47-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="3dc47-240">**enhet** Adress till den enhets behållare som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="3dc47-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-241">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-241">Return Values</span></span>

- <span data-ttu-id="3dc47-242">**UX_SUCCESS** (0x00) enhets containern finns och returneras</span><span class="sxs-lookup"><span data-stu-id="3dc47-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="3dc47-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Okänd enhet</span><span class="sxs-lookup"><span data-stu-id="3dc47-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-244">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="3dc47-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="3dc47-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="3dc47-246">Hämta en slut punkts behållare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-247">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="3dc47-248">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-248">Description</span></span>

<span data-ttu-id="3dc47-249">Den här funktionen returnerar en slut punkts behållare baserat på gränssnitts referensen och ett slut punkts index.</span><span class="sxs-lookup"><span data-stu-id="3dc47-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="3dc47-250">Det förutsätts att den alternativa inställningen för gränssnittet har marker ATS eller att standardinställningen används innan de slut punkter som genomsöks.</span><span class="sxs-lookup"><span data-stu-id="3dc47-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-251">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-251">Parameters</span></span>

- <span data-ttu-id="3dc47-252">**gränssnitt** Pekare till den gränssnitts behållare som innehåller den begärda slut punkten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="3dc47-253">**endpoint_index** Index för slut punkten i det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="3dc47-254">**slut punkt** Adress till den slut punkts behållare som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="3dc47-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-255">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-255">Return Values</span></span>

- <span data-ttu-id="3dc47-256">**UX_SUCCESS** (0x00) slut punkts containern finns och returneras.</span><span class="sxs-lookup"><span data-stu-id="3dc47-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="3dc47-257">Det angivna **UX_INTERFACE_HANDLE_UNKNOWN** -gränssnittet (0x52) finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="3dc47-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0X53) slut punkts indexet finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-259">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="3dc47-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="3dc47-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="3dc47-261">Registrera en USB-styrenhet i USB-stacken.</span><span class="sxs-lookup"><span data-stu-id="3dc47-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-262">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="3dc47-263">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-263">Description</span></span>

<span data-ttu-id="3dc47-264">Den här funktionen registrerar en USB-styrenhet till USB-stacken.</span><span class="sxs-lookup"><span data-stu-id="3dc47-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="3dc47-265">Det allokerar främst det minne som används av den här styrenheten och skickar initierings kommandot till kontrollanten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-266">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-266">Parameters</span></span>

- <span data-ttu-id="3dc47-267">**hcd_name** Namn på värd styrenheten</span><span class="sxs-lookup"><span data-stu-id="3dc47-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="3dc47-268">**hcd_function** Funktionen i värd styrenheten som ansvarar för initieringen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="3dc47-269">**hcd_param1** Den IO-eller minnes resurs som används av HCD.</span><span class="sxs-lookup"><span data-stu-id="3dc47-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="3dc47-270">**hcd_param2** IRQ som används av värd styrenheten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-271">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-271">Return Values</span></span>

- <span data-ttu-id="3dc47-272">**UX_SUCCESS** (0x00) kontrollanten initierades korrekt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="3dc47-273">**UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för den här styrenheten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="3dc47-274">**UX_PORT_RESET_FAILED** (0X31) Det gick inte att återställa kontrollanten.</span><span class="sxs-lookup"><span data-stu-id="3dc47-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="3dc47-275">**UX_CONTROLLER_INIT_FAILED** (0x32) styrenheten kunde inte initieras korrekt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-276">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="3dc47-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="3dc47-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="3dc47-278">Hämta en gränssnitts container pekare.</span><span class="sxs-lookup"><span data-stu-id="3dc47-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-279">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="3dc47-280">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-280">Description</span></span>

<span data-ttu-id="3dc47-281">Den här funktionen returnerar en gränssnitts behållare baserat på en konfigurations referens, ett gränssnitts index och ett alternativ inställnings index.</span><span class="sxs-lookup"><span data-stu-id="3dc47-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-282">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-282">Parameters</span></span>

- <span data-ttu-id="3dc47-283">**konfiguration** Pekare till den konfigurations behållare som äger gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="3dc47-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="3dc47-284">**interface_index** Gränssnitts index som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="3dc47-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="3dc47-285">**alternate_setting_index** Alternativ i det gränssnitt som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="3dc47-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="3dc47-286">**gränssnitt** Adress till den gränssnitts container pekare som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="3dc47-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-287">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-287">Return Values</span></span>

- <span data-ttu-id="3dc47-288">**UX_SUCCESS** (0x00) gränssnitts behållaren för gränssnitts indexet och den alternativa inställningen hittades och returnerades.</span><span class="sxs-lookup"><span data-stu-id="3dc47-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="3dc47-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) konfigurationen finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="3dc47-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) gränssnittet finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-291">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="3dc47-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="3dc47-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="3dc47-293">Välj en alternativ inställning för ett gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-294">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="3dc47-295">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-295">Description</span></span>

<span data-ttu-id="3dc47-296">Den här funktionen väljer en specifik alternativ inställning för ett angivet gränssnitt som tillhör den valda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="3dc47-297">Den här funktionen används för att ändra från standard alternativ inställningen till en ny inställning eller att gå tillbaka till standard alternativ inställningen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="3dc47-298">När en ny alternativ inställning väljs, är tidigare slut punkts egenskaper ogiltiga och bör läsas in igen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3dc47-299">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="3dc47-299">Input Parameter</span></span>

- <span data-ttu-id="3dc47-300">**gränssnitt** Pekar till gränssnitts behållaren vars alternativa inställning ska väljas.</span><span class="sxs-lookup"><span data-stu-id="3dc47-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-301">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-301">Return Values</span></span>

- <span data-ttu-id="3dc47-302">**UX_SUCCESS** (0X00) den alternativa inställningen för det här gränssnittet har marker ATS.</span><span class="sxs-lookup"><span data-stu-id="3dc47-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="3dc47-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) gränssnittet finns inte.</span><span class="sxs-lookup"><span data-stu-id="3dc47-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-304">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="3dc47-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="3dc47-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="3dc47-306">Avbryt en väntande överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="3dc47-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-307">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="3dc47-308">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-308">Description</span></span>

<span data-ttu-id="3dc47-309">Den här funktionen avbryter en väntande överförings förfrågan som redan har skickats.</span><span class="sxs-lookup"><span data-stu-id="3dc47-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="3dc47-310">Den här funktionen avbryter bara en begäran om överföring.</span><span class="sxs-lookup"><span data-stu-id="3dc47-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="3dc47-311">Anropet till funktionen kommer att ha statusen UX_TRANSFER REQUEST_STATUS_ABORT.</span><span class="sxs-lookup"><span data-stu-id="3dc47-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="3dc47-312">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3dc47-312">Parameters</span></span>

- <span data-ttu-id="3dc47-313">**överförings förfrågan** Pekare till överförings förfrågan som ska avbrytas.</span><span class="sxs-lookup"><span data-stu-id="3dc47-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-314">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-314">Return Values</span></span>

- <span data-ttu-id="3dc47-315">**UX_SUCCESS** (0X00) USB-överföringen för den här överföringsbegäran har avbrutits.</span><span class="sxs-lookup"><span data-stu-id="3dc47-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-316">Exempel</span><span class="sxs-lookup"><span data-stu-id="3dc47-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="3dc47-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="3dc47-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="3dc47-318">Begär en USB-överföring.</span><span class="sxs-lookup"><span data-stu-id="3dc47-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="3dc47-319">Prototyp</span><span class="sxs-lookup"><span data-stu-id="3dc47-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="3dc47-320">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3dc47-320">Description</span></span>

<span data-ttu-id="3dc47-321">Den här funktionen utför en USB-transaktion.</span><span class="sxs-lookup"><span data-stu-id="3dc47-321">This function performs a USB transaction.</span></span> <span data-ttu-id="3dc47-322">Vid inmatning ger överföringsbegäran den valda slut punkts pipe för den här transaktionen och de parametrar som är kopplade till överföringen (data nytto Last, transaktions längd).</span><span class="sxs-lookup"><span data-stu-id="3dc47-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="3dc47-323">För Control pipe blockeras transaktionen och kommer bara att returneras när de tre faserna av kontroll överföringen har slutförts eller om det finns ett tidigare fel.</span><span class="sxs-lookup"><span data-stu-id="3dc47-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="3dc47-324">För andra pipes kommer USB-stacken att schemalägga transaktionen på USB-enheten, men väntar inte på slut för ande.</span><span class="sxs-lookup"><span data-stu-id="3dc47-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="3dc47-325">Varje överföringsbegäran för icke-blockerande pipes måste ange en rutin hanterare för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="3dc47-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="3dc47-326">När funktions anropet returnerar, bör statusen för överförings förfrågan undersökas eftersom den innehåller resultatet av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3dc47-327">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="3dc47-327">Input Parameter</span></span>

- <span data-ttu-id="3dc47-328">**transfer_request** Pekare till överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="3dc47-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="3dc47-329">Överföringsbegäran innehåller all nödvändig information som krävs för överföringen.</span><span class="sxs-lookup"><span data-stu-id="3dc47-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3dc47-330">Retur värden</span><span class="sxs-lookup"><span data-stu-id="3dc47-330">Return Values</span></span>

- <span data-ttu-id="3dc47-331">**UX_SUCCESS** (0X00) USB-överföringen av denna överföringsbegäran schemalades korrekt.</span><span class="sxs-lookup"><span data-stu-id="3dc47-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="3dc47-332">Status koden för överföringsbegäran bör undersökas när överföringsbegäran slutförs.</span><span class="sxs-lookup"><span data-stu-id="3dc47-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="3dc47-333">**UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för att allokera nödvändiga styrenhets resurser.</span><span class="sxs-lookup"><span data-stu-id="3dc47-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="3dc47-334">**UX_TRANSFER_NOT_READY** (0x25) enheten var i ett ogiltigt tillstånd – måste vara ansluten, adresserad eller konfigurerad.</span><span class="sxs-lookup"><span data-stu-id="3dc47-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="3dc47-335">Exempel:</span><span class="sxs-lookup"><span data-stu-id="3dc47-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
