---
title: Kapitel 5 – USBX värd klasser API
description: 'Lär dig mer om API: et för värd klasser för USBX.'
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828620"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="90acc-103">Kapitel 5 – USBX värd klasser API</span><span class="sxs-lookup"><span data-stu-id="90acc-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="90acc-104">I det här kapitlet beskrivs alla exponerade API: er för USBX-värd klasser.</span><span class="sxs-lookup"><span data-stu-id="90acc-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="90acc-105">Följande API: er för varje klass beskrivs i detalj.</span><span class="sxs-lookup"><span data-stu-id="90acc-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="90acc-106">HID-klass</span><span class="sxs-lookup"><span data-stu-id="90acc-106">HID class</span></span>
- <span data-ttu-id="90acc-107">CDC-ACM-klass</span><span class="sxs-lookup"><span data-stu-id="90acc-107">CDC-ACM class</span></span>
- <span data-ttu-id="90acc-108">CDC-ECM-klass</span><span class="sxs-lookup"><span data-stu-id="90acc-108">CDC-ECM class</span></span>
- <span data-ttu-id="90acc-109">Lagrings klass</span><span class="sxs-lookup"><span data-stu-id="90acc-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="90acc-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="90acc-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="90acc-111">Registrera en HID-klient i HID-klassen.</span><span class="sxs-lookup"><span data-stu-id="90acc-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-112">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="90acc-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-113">Description</span></span>

<span data-ttu-id="90acc-114">Den här funktionen används för att registrera en HID-klient i HID-klassen.</span><span class="sxs-lookup"><span data-stu-id="90acc-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="90acc-115">HID-klassen behöver hitta en matchning mellan en HID-enhet och HID-klient innan data begärs från den här enheten.</span><span class="sxs-lookup"><span data-stu-id="90acc-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="90acc-116">C-strängen för hid_client_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="90acc-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-117">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-117">Parameters</span></span>

- <span data-ttu-id="90acc-118">**hid_client_name** Pekar på HID-klientcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="90acc-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="90acc-119">**hid_client_handler** Pekar mot HID-klient hanteraren.</span><span class="sxs-lookup"><span data-stu-id="90acc-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-120">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-120">Return Values</span></span>

- <span data-ttu-id="90acc-121">**UX_SUCCESS** (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="90acc-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="90acc-122">**UX_MEMORY_INSUFFICIENT** -minnesallokering (0x12) för klienten misslyckades.</span><span class="sxs-lookup"><span data-stu-id="90acc-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="90acc-123">**UX_MEMORY_ARRAY_FULL** (0X1a) högsta antal klienter som redan har registrerats.</span><span class="sxs-lookup"><span data-stu-id="90acc-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="90acc-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0X58) den här klassen finns redan</span><span class="sxs-lookup"><span data-stu-id="90acc-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="90acc-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="90acc-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="90acc-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="90acc-127">Registrera ett motanrop från HID-klassen.</span><span class="sxs-lookup"><span data-stu-id="90acc-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-128">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="90acc-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-129">Description</span></span>

<span data-ttu-id="90acc-130">Den här funktionen används för att registrera ett motanrop från HID-klassen till HID-klienten när en rapport tas emot.</span><span class="sxs-lookup"><span data-stu-id="90acc-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-131">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-131">Parameters</span></span>

- <span data-ttu-id="90acc-132">**HID** Pekare till HID-klassdrivrutinen</span><span class="sxs-lookup"><span data-stu-id="90acc-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="90acc-133">**call_back** Pekare till call_back-strukturen</span><span class="sxs-lookup"><span data-stu-id="90acc-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-134">Returvärden</span><span class="sxs-lookup"><span data-stu-id="90acc-134">Return values</span></span>

- <span data-ttu-id="90acc-135">**UX_SUCCESS** (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="90acc-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="90acc-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b) ogiltig HID-instans.</span><span class="sxs-lookup"><span data-stu-id="90acc-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="90acc-137">**UX_HOST_CLASS_HID_REPORT_ERROR** -fel (0x79) i rapportens återanrops registrering.</span><span class="sxs-lookup"><span data-stu-id="90acc-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="90acc-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="90acc-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="90acc-140">Starta den periodiska slut punkten för en HID-klass instans.</span><span class="sxs-lookup"><span data-stu-id="90acc-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-141">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="90acc-142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-142">Description</span></span>

<span data-ttu-id="90acc-143">Den här funktionen används för att starta den periodiska (avbryta) slut punkten för instansen av HID-klassen som är kopplad till den här HID-klienten.</span><span class="sxs-lookup"><span data-stu-id="90acc-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="90acc-144">HID-klassen kan inte starta den periodiska slut punkten förrän HID-klienten har Aktiver ATS och därför lämnas den till HID-klienten för att starta slut punkten för att ta emot rapporter.</span><span class="sxs-lookup"><span data-stu-id="90acc-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="90acc-145">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="90acc-145">Input Parameter</span></span>

- <span data-ttu-id="90acc-146">**HID** Pekare till klass instansen HID.</span><span class="sxs-lookup"><span data-stu-id="90acc-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-147">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-147">Return Values</span></span>

- <span data-ttu-id="90acc-148">**UX_SUCCESS** (0X00) periodisk rapportering har startats.</span><span class="sxs-lookup"><span data-stu-id="90acc-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="90acc-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** -fel (0x7A) i den periodiska rapporten.</span><span class="sxs-lookup"><span data-stu-id="90acc-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="90acc-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="90acc-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="90acc-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="90acc-153">Stoppa den periodiska slut punkten för en HID-klass instans.</span><span class="sxs-lookup"><span data-stu-id="90acc-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="90acc-155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-155">Description</span></span>

<span data-ttu-id="90acc-156">Den här funktionen används för att stoppa den periodiska (avbryta) slut punkten för instansen av HID-klassen som är kopplad till den här HID-klienten.</span><span class="sxs-lookup"><span data-stu-id="90acc-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="90acc-157">Den HID-klassen kan inte stoppa den periodiska slut punkten förrän HID-klienten är inaktive rad, men alla dess resurser är frigjorde och de lämnas därför till HID-klienten för att stoppa slut punkten.</span><span class="sxs-lookup"><span data-stu-id="90acc-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="90acc-158">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="90acc-158">Input Parameter</span></span>

- <span data-ttu-id="90acc-159">**HID** Pekare till klass instansen HID.</span><span class="sxs-lookup"><span data-stu-id="90acc-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-160">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-160">Return Values</span></span>

- <span data-ttu-id="90acc-161">**UX_SUCCESS** (0X00) periodisk rapportering har stoppats.</span><span class="sxs-lookup"><span data-stu-id="90acc-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="90acc-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** -fel (0x7A) i den periodiska rapporten.</span><span class="sxs-lookup"><span data-stu-id="90acc-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="90acc-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas</span><span class="sxs-lookup"><span data-stu-id="90acc-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="90acc-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="90acc-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="90acc-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="90acc-166">Hämta en rapport från en HID-klass instans.</span><span class="sxs-lookup"><span data-stu-id="90acc-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-167">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="90acc-168">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-168">Description</span></span>

<span data-ttu-id="90acc-169">Den här funktionen används för att ta emot en rapport direkt från enheten utan att förlita dig på den periodiska slut punkten.</span><span class="sxs-lookup"><span data-stu-id="90acc-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="90acc-170">Den här rapporten kommer från kontroll slut punkten, men dess behandling är densamma som om den var den periodiska slut punkten.</span><span class="sxs-lookup"><span data-stu-id="90acc-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-171">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-171">Parameters</span></span>

- <span data-ttu-id="90acc-172">**HID** Pekare till klass instansen HID.</span><span class="sxs-lookup"><span data-stu-id="90acc-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="90acc-173">**client_report** Pekare till rapporten HID client.</span><span class="sxs-lookup"><span data-stu-id="90acc-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-174">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-174">Return Values</span></span>

- <span data-ttu-id="90acc-175">**UX_SUCCESS** (0x00) rapporten har tagits emot.</span><span class="sxs-lookup"><span data-stu-id="90acc-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="90acc-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0X70) antingen var klient rapporten ogiltig eller uppstod vid överföring.</span><span class="sxs-lookup"><span data-stu-id="90acc-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="90acc-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="90acc-178">**UX_BUFFER_OVERFLOW** (0X5d) den angivna bufferten är inte tillräckligt stor för att rymma den okomprimerade rapporten.</span><span class="sxs-lookup"><span data-stu-id="90acc-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-179">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="90acc-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="90acc-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="90acc-181">Skicka en rapport</span><span class="sxs-lookup"><span data-stu-id="90acc-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-182">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="90acc-183">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-183">Description</span></span>

<span data-ttu-id="90acc-184">Den här funktionen används för att skicka en rapport direkt till enheten.</span><span class="sxs-lookup"><span data-stu-id="90acc-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-185">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-185">Parameters</span></span>

- <span data-ttu-id="90acc-186">**HID** Pekare till klass instansen HID.</span><span class="sxs-lookup"><span data-stu-id="90acc-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="90acc-187">**client_report** Pekare till rapporten HID client.</span><span class="sxs-lookup"><span data-stu-id="90acc-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-188">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-188">Return Values</span></span>

- <span data-ttu-id="90acc-189">**UX_SUCCESS** (0x00) rapporten har skickats.</span><span class="sxs-lookup"><span data-stu-id="90acc-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="90acc-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0X70) antingen var klient rapporten ogiltig eller uppstod vid överföring.</span><span class="sxs-lookup"><span data-stu-id="90acc-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="90acc-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="90acc-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0X5d) den angivna bufferten är inte tillräckligt stor för att rymma den okomprimerade rapporten.</span><span class="sxs-lookup"><span data-stu-id="90acc-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-193">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="90acc-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="90acc-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="90acc-195">Hämta mus knappar.</span><span class="sxs-lookup"><span data-stu-id="90acc-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-196">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="90acc-197">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-197">Description</span></span>

<span data-ttu-id="90acc-198">Den här funktionen används för att hämta mus knappar</span><span class="sxs-lookup"><span data-stu-id="90acc-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-199">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-199">Parameters</span></span>

- <span data-ttu-id="90acc-200">**mouse_instance** Pekare till HID Mouse-instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="90acc-201">**mouse_buttons** Pekare till retur knapparna.</span><span class="sxs-lookup"><span data-stu-id="90acc-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-202">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-202">Return Values</span></span>

- <span data-ttu-id="90acc-203">Mus knappen **UX_SUCCESS** (0x00) har hämtats.</span><span class="sxs-lookup"><span data-stu-id="90acc-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="90acc-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-205">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="90acc-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="90acc-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="90acc-207">Hämta mus position.</span><span class="sxs-lookup"><span data-stu-id="90acc-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-208">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="90acc-209">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-209">Description</span></span>

<span data-ttu-id="90acc-210">Den här funktionen används för att hämta markörens position i x & y-koordinater.</span><span class="sxs-lookup"><span data-stu-id="90acc-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-211">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-211">Parameters</span></span>

- <span data-ttu-id="90acc-212">**mouse_instance** Pekare till HID Mouse-instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="90acc-213">**mouse_x_position** Pekar mot x-koordinaten.</span><span class="sxs-lookup"><span data-stu-id="90acc-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="90acc-214">**mouse_y_position** Pekare till y-koordinaten.</span><span class="sxs-lookup"><span data-stu-id="90acc-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-215">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-215">Return Values</span></span>

- <span data-ttu-id="90acc-216">**UX_SUCCESS** (0X00) X &amp; Y-koordinaterna har hämtats.</span><span class="sxs-lookup"><span data-stu-id="90acc-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="90acc-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-218">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="90acc-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="90acc-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="90acc-220">Hämta tangent bords nyckel och tillstånd.</span><span class="sxs-lookup"><span data-stu-id="90acc-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-221">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="90acc-222">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-222">Description</span></span>

<span data-ttu-id="90acc-223">Den här funktionen används för att hämta tangent bords nyckel och tillstånd.</span><span class="sxs-lookup"><span data-stu-id="90acc-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-224">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-224">Parameters</span></span>

- <span data-ttu-id="90acc-225">**keyboard_instance** Pekare till HID Keyboard-instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="90acc-226">**keyboard_key** Pekare till tangent bords nyckel behållare.</span><span class="sxs-lookup"><span data-stu-id="90acc-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="90acc-227">**keyboard_state** Pekare till behållaren med tangent bords tillstånd.</span><span class="sxs-lookup"><span data-stu-id="90acc-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-228">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-228">Return Values</span></span>

- <span data-ttu-id="90acc-229">Nyckel och tillstånd för **UX_SUCCESS** (0x00) har hämtats.</span><span class="sxs-lookup"><span data-stu-id="90acc-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="90acc-230">**UX_ERROR** (0Xff) inget att rapportera.</span><span class="sxs-lookup"><span data-stu-id="90acc-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="90acc-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="90acc-232">Tangent bords status kan ha följande värden.</span><span class="sxs-lookup"><span data-stu-id="90acc-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="90acc-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span><span class="sxs-lookup"><span data-stu-id="90acc-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="90acc-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span><span class="sxs-lookup"><span data-stu-id="90acc-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="90acc-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="90acc-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="90acc-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span><span class="sxs-lookup"><span data-stu-id="90acc-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="90acc-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span><span class="sxs-lookup"><span data-stu-id="90acc-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="90acc-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span><span class="sxs-lookup"><span data-stu-id="90acc-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="90acc-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span><span class="sxs-lookup"><span data-stu-id="90acc-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="90acc-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span><span class="sxs-lookup"><span data-stu-id="90acc-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="90acc-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span><span class="sxs-lookup"><span data-stu-id="90acc-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="90acc-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span><span class="sxs-lookup"><span data-stu-id="90acc-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="90acc-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span><span class="sxs-lookup"><span data-stu-id="90acc-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="90acc-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span><span class="sxs-lookup"><span data-stu-id="90acc-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="90acc-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span><span class="sxs-lookup"><span data-stu-id="90acc-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="90acc-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span><span class="sxs-lookup"><span data-stu-id="90acc-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="90acc-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span><span class="sxs-lookup"><span data-stu-id="90acc-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="90acc-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span><span class="sxs-lookup"><span data-stu-id="90acc-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="90acc-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span><span class="sxs-lookup"><span data-stu-id="90acc-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="90acc-250">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="90acc-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="90acc-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="90acc-252">Utföra en IOCTL-funktion på HID-tangentbordet.</span><span class="sxs-lookup"><span data-stu-id="90acc-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-253">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="90acc-254">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-254">Description</span></span>

<span data-ttu-id="90acc-255">Den här funktionen utför en angiven IOCTL-funktion på HID-tangentbordet.</span><span class="sxs-lookup"><span data-stu-id="90acc-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="90acc-256">Anropet blockeras och returneras bara när det uppstår ett fel eller när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-257">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-257">Parameters</span></span>

- <span data-ttu-id="90acc-258">**keyboard_instance** Pekare till HID Keyboard-instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="90acc-259">den **ioctl_function** IOCTL-funktion som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="90acc-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="90acc-260">Se tabellen nedan för en av de tillåtna IOCTL-funktionerna.</span><span class="sxs-lookup"><span data-stu-id="90acc-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="90acc-261">**parameter** Pekar mot en parameter som är speciell för IOCTL.</span><span class="sxs-lookup"><span data-stu-id="90acc-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-262">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-262">Return Values</span></span>

- <span data-ttu-id="90acc-263">**UX_SUCCESS** (0x00) IOCTL-funktionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="90acc-264">**UX_FUNCTION_NOT_SUPPORTED** (0X54) Okänd IOCTL-funktion</span><span class="sxs-lookup"><span data-stu-id="90acc-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="90acc-265">IOCTL-funktioner</span><span class="sxs-lookup"><span data-stu-id="90acc-265">IOCTL functions</span></span>

- <span data-ttu-id="90acc-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="90acc-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="90acc-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="90acc-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="90acc-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="90acc-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="90acc-269">Exempel – ändra tangentbordslayout</span><span class="sxs-lookup"><span data-stu-id="90acc-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="90acc-270">Exempel – inaktivera tangent bords kryptering</span><span class="sxs-lookup"><span data-stu-id="90acc-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="90acc-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="90acc-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="90acc-272">Hämta fjärr styrnings användning</span><span class="sxs-lookup"><span data-stu-id="90acc-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-273">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="90acc-274">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-274">Description</span></span>

<span data-ttu-id="90acc-275">Den här funktionen används för att hämta fjärr styrnings användningen.</span><span class="sxs-lookup"><span data-stu-id="90acc-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-276">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-276">Parameters</span></span>

- <span data-ttu-id="90acc-277">**remote_control_instance** Pekar på HID-fjärrkontroll-instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="90acc-278">**användning** Pekar på användningen.</span><span class="sxs-lookup"><span data-stu-id="90acc-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="90acc-279">**värde** Pekar till värdet för användningen.</span><span class="sxs-lookup"><span data-stu-id="90acc-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-280">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-280">Return Values</span></span>

- <span data-ttu-id="90acc-281">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="90acc-282">**UX_ERROR** (0Xff) inget att rapportera.</span><span class="sxs-lookup"><span data-stu-id="90acc-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="90acc-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) HID-tjänstinstans saknas.</span><span class="sxs-lookup"><span data-stu-id="90acc-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="90acc-284">Listan över alla möjliga användnings områden är för lång för att få plats i den här användar handboken.</span><span class="sxs-lookup"><span data-stu-id="90acc-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="90acc-285">För en fullständig beskrivning har ux_host_class_hid. h hela uppsättningen möjliga värden.</span><span class="sxs-lookup"><span data-stu-id="90acc-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-286">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="90acc-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="90acc-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="90acc-288">Läs från cdc_acm-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="90acc-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-289">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="90acc-290">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-290">Description</span></span>

<span data-ttu-id="90acc-291">Den här funktionen läser från cdc_acm-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="90acc-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="90acc-292">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="90acc-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-293">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-293">Parameters</span></span>

- <span data-ttu-id="90acc-294">**cdc_acm** Pekare till cdc_acm klass instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="90acc-295">**data_pointer** Pekar till buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="90acc-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="90acc-296">**requested_length** Längd att ta emot.</span><span class="sxs-lookup"><span data-stu-id="90acc-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="90acc-297">**actual_length** Den längd som faktiskt mottagits.</span><span class="sxs-lookup"><span data-stu-id="90acc-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-298">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-298">Return Values</span></span>

- <span data-ttu-id="90acc-299">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="90acc-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) cdc_acm instansen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="90acc-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="90acc-301">**UX_TRANSFER_TIMEOUT** (0x5c) timeout för överföring, Läs ofullständig.</span><span class="sxs-lookup"><span data-stu-id="90acc-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-302">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="90acc-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="90acc-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="90acc-304">Skriv till cdc_acm gränssnittet</span><span class="sxs-lookup"><span data-stu-id="90acc-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-305">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="90acc-306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-306">Description</span></span>

<span data-ttu-id="90acc-307">Den här funktionen skriver till cdc_acm-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="90acc-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="90acc-308">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="90acc-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-309">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-309">Parameters</span></span>

- <span data-ttu-id="90acc-310">**cdc_acm** Pekare till cdc_acm klass instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="90acc-311">**data_pointer** Pekar till buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="90acc-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="90acc-312">**requested_length** Längd som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="90acc-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="90acc-313">**actual_length** Den längd som faktiskt har skickats.</span><span class="sxs-lookup"><span data-stu-id="90acc-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="90acc-314">Retur värden</span><span class="sxs-lookup"><span data-stu-id="90acc-314">Return Values</span></span>

- <span data-ttu-id="90acc-315">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="90acc-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) cdc_acm instansen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="90acc-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="90acc-317">**UX_TRANSFER_TIMEOUT** (0X5c) överförings tids gräns, skrivning ofullständig.</span><span class="sxs-lookup"><span data-stu-id="90acc-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="90acc-318">Exempel</span><span class="sxs-lookup"><span data-stu-id="90acc-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="90acc-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="90acc-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="90acc-320">Utföra en IOCTL-funktion på cdc_acm-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="90acc-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-321">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="90acc-322">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-322">Description</span></span>

<span data-ttu-id="90acc-323">Den här funktionen utför en angiven IOCTL-funktion till cdc_acm-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="90acc-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="90acc-324">Anropet blockeras och returneras bara när det uppstår ett fel eller när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-325">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-325">Parameters</span></span>

- <span data-ttu-id="90acc-326">**cdc_acm** Pekare till cdc_acm klass instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="90acc-327">den **ioctl_function** IOCTL-funktion som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="90acc-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="90acc-328">Se tabellen nedan för en av de tillåtna IOCTL-funktionerna.</span><span class="sxs-lookup"><span data-stu-id="90acc-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="90acc-329">**parameter** Pekare till en parameter som är speciell för IOCTL</span><span class="sxs-lookup"><span data-stu-id="90acc-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="90acc-330">Returvärde</span><span class="sxs-lookup"><span data-stu-id="90acc-330">Return Value</span></span>

- <span data-ttu-id="90acc-331">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="90acc-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="90acc-332">**UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne.</span><span class="sxs-lookup"><span data-stu-id="90acc-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="90acc-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5B) CDC-ACM-instansen är i ett ogiltigt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="90acc-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="90acc-334">**UX_FUNCTION_NOT_SUPPORTED** (0X54) Okänd IOCTL-funktion.</span><span class="sxs-lookup"><span data-stu-id="90acc-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="90acc-335">IOCTL-funktioner:</span><span class="sxs-lookup"><span data-stu-id="90acc-335">IOCTL functions:</span></span>

- <span data-ttu-id="90acc-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="90acc-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="90acc-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="90acc-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="90acc-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="90acc-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="90acc-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="90acc-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="90acc-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="90acc-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="90acc-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="90acc-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="90acc-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="90acc-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="90acc-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="90acc-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="90acc-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="90acc-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="90acc-345">Börjar ta emot data i bakgrunden från enheten.</span><span class="sxs-lookup"><span data-stu-id="90acc-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-346">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="90acc-347">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-347">Description</span></span>

<span data-ttu-id="90acc-348">Den här funktionen gör att USBX kontinuerligt läser data från enheten i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="90acc-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="90acc-349">Vid slutförandet av varje transaktion anropas det motanrop som anges i **cdc_acm_reception** så att programmet kan utföra ytterligare bearbetning av transaktionens data.</span><span class="sxs-lookup"><span data-stu-id="90acc-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="90acc-350">**ux_host_class_cdc_acm_read** får inte användas när bakgrunds mottagning används.</span><span class="sxs-lookup"><span data-stu-id="90acc-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-351">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-351">Parameters</span></span>

- <span data-ttu-id="90acc-352">**cdc_acm** Pekare till cdc_acm klass instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="90acc-353">**cdc_acm_reception** Pekare till parameter som innehåller värden som definierar bakgrunds mottagning.</span><span class="sxs-lookup"><span data-stu-id="90acc-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="90acc-354">Layouten för den här parametern följer:</span><span class="sxs-lookup"><span data-stu-id="90acc-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="90acc-355">Returvärde</span><span class="sxs-lookup"><span data-stu-id="90acc-355">Return Value</span></span>

- <span data-ttu-id="90acc-356">**UX_SUCCESS** (0x00) bakgrunds mottagning har startats.</span><span class="sxs-lookup"><span data-stu-id="90acc-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="90acc-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0X5b) fel klass instans.</span><span class="sxs-lookup"><span data-stu-id="90acc-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="90acc-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="90acc-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="90acc-359">Stoppar bakgrunds mottagning av paket.</span><span class="sxs-lookup"><span data-stu-id="90acc-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="90acc-360">Prototyp</span><span class="sxs-lookup"><span data-stu-id="90acc-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="90acc-361">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90acc-361">Description</span></span>

<span data-ttu-id="90acc-362">Den här funktionen gör att USBX stoppar bakgrunds mottagning som tidigare påbörjats av **ux_host_class_cdc_acm_reception_start**.</span><span class="sxs-lookup"><span data-stu-id="90acc-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="90acc-363">Parametrar</span><span class="sxs-lookup"><span data-stu-id="90acc-363">Parameters</span></span>

- <span data-ttu-id="90acc-364">**cdc_acm** Pekare till cdc_acm klass instansen.</span><span class="sxs-lookup"><span data-stu-id="90acc-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="90acc-365">**cdc_acm_reception** Pekar till samma parameter som användes för att starta bakgrunds mottagning.</span><span class="sxs-lookup"><span data-stu-id="90acc-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="90acc-366">Layouten för den här parametern följer:</span><span class="sxs-lookup"><span data-stu-id="90acc-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="90acc-367">Returvärde</span><span class="sxs-lookup"><span data-stu-id="90acc-367">Return Value</span></span>

- <span data-ttu-id="90acc-368">**UX_SUCCESS** (0x00) bakgrunds mottagning har stoppats.</span><span class="sxs-lookup"><span data-stu-id="90acc-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="90acc-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0X5b) fel klass instans.</span><span class="sxs-lookup"><span data-stu-id="90acc-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
