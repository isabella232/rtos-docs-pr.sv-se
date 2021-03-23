---
title: API för USBX-värd klasser
description: 'I det här kapitlet beskrivs alla exponerade API: er för USBX-värd klasser.'
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828113"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="b3b25-103">Kapitel 2: API för USBX-värd klasser</span><span class="sxs-lookup"><span data-stu-id="b3b25-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="b3b25-104">I det här kapitlet beskrivs alla exponerade API: er för USBX-värd klasser.</span><span class="sxs-lookup"><span data-stu-id="b3b25-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="b3b25-105">Följande API: er för varje klass beskrivs i detalj.</span><span class="sxs-lookup"><span data-stu-id="b3b25-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="b3b25-106">Skrivar klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-106">Printer class</span></span>
- <span data-ttu-id="b3b25-107">Ljud klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-107">Audio class</span></span>
- <span data-ttu-id="b3b25-108">Asix-klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-108">Asix class</span></span>
- <span data-ttu-id="b3b25-109">Pima/PTP-klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-109">Pima/PTP class</span></span>
- <span data-ttu-id="b3b25-110">Prolific-klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-110">Prolific class</span></span>
- <span data-ttu-id="b3b25-111">Generisk serie klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="b3b25-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="b3b25-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="b3b25-113">Läsa från skrivar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-114">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-115">Description</span></span>

<span data-ttu-id="b3b25-116">Den här funktionen läser från skrivar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-116">This function reads from the printer interface.</span></span> <span data-ttu-id="b3b25-117">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="b3b25-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="b3b25-118">En läsning tillåts bara på dubbelriktade skrivare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-119">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-119">Parameters</span></span>

- <span data-ttu-id="b3b25-120">**skrivare**: pekar på skrivarens klass instans.</span><span class="sxs-lookup"><span data-stu-id="b3b25-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="b3b25-121">**data_pointer**: pekar mot buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="b3b25-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="b3b25-122">**requested_length**: längden som ska tas emot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="b3b25-123">**actual_length**: den längd som faktiskt mottagits.</span><span class="sxs-lookup"><span data-stu-id="b3b25-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-124">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-124">Return Value</span></span>

- <span data-ttu-id="b3b25-125">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-126">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funktionen stöds inte eftersom skrivaren inte är dubbelriktad.</span><span class="sxs-lookup"><span data-stu-id="b3b25-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="b3b25-127">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, Läsning ofullständig.</span><span class="sxs-lookup"><span data-stu-id="b3b25-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="b3b25-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="b3b25-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="b3b25-130">Skriv till skrivar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-131">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-132">Description</span></span>

<span data-ttu-id="b3b25-133">Den här funktionen skriver till skrivar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-133">This function writes to the printer interface.</span></span> <span data-ttu-id="b3b25-134">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="b3b25-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-135">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-135">Parameters</span></span>

- <span data-ttu-id="b3b25-136">**skrivare**: pekar på skrivarens klass instans.</span><span class="sxs-lookup"><span data-stu-id="b3b25-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="b3b25-137">**data_pointer**: pekar mot buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="b3b25-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="b3b25-138">**requested_length**: längden som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="b3b25-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="b3b25-139">**actual_length**: den längd som faktiskt har skickats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-140">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-140">Return Value</span></span>

- <span data-ttu-id="b3b25-141">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-142">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, skrivning ofullständig.</span><span class="sxs-lookup"><span data-stu-id="b3b25-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-143">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="b3b25-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="b3b25-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="b3b25-145">Utför en mjuk återställning till skrivaren.</span><span class="sxs-lookup"><span data-stu-id="b3b25-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-146">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="b3b25-147">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-147">Description</span></span>

<span data-ttu-id="b3b25-148">Den här funktionen utför en mjuk återställning till skrivaren.</span><span class="sxs-lookup"><span data-stu-id="b3b25-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="b3b25-149">Indataparameter</span><span class="sxs-lookup"><span data-stu-id="b3b25-149">Input Parameter</span></span>

- <span data-ttu-id="b3b25-150">**skrivare**: pekar på skrivarens klass instans.</span><span class="sxs-lookup"><span data-stu-id="b3b25-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-151">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-151">Return Value</span></span>

- <span data-ttu-id="b3b25-152">**UX_SUCCESS**: (0x00) återställningen slutfördes.</span><span class="sxs-lookup"><span data-stu-id="b3b25-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="b3b25-153">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, återställning är inte slutförd.</span><span class="sxs-lookup"><span data-stu-id="b3b25-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="b3b25-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="b3b25-156">Hämta skrivar status</span><span class="sxs-lookup"><span data-stu-id="b3b25-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-157">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="b3b25-158">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-158">Description</span></span>

<span data-ttu-id="b3b25-159">Den här funktionen hämtar skrivarens status.</span><span class="sxs-lookup"><span data-stu-id="b3b25-159">This function obtains the printer status.</span></span> <span data-ttu-id="b3b25-160">Skrivarens status liknar LPT-statusen (1284 standard).</span><span class="sxs-lookup"><span data-stu-id="b3b25-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-161">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-161">Parameters</span></span>

- <span data-ttu-id="b3b25-162">**skrivare**: pekar på skrivarens klass instans.</span><span class="sxs-lookup"><span data-stu-id="b3b25-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="b3b25-163">**printer_status**: adress till den status som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="b3b25-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-164">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-164">Return Value</span></span>

- <span data-ttu-id="b3b25-165">**UX_SUCCESS** (0x00): återställningen slutfördes.</span><span class="sxs-lookup"><span data-stu-id="b3b25-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="b3b25-166">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="b3b25-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="b3b25-167">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, återställning är inte slutförd</span><span class="sxs-lookup"><span data-stu-id="b3b25-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-168">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="b3b25-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="b3b25-170">Hämta skrivarens enhets-ID.</span><span class="sxs-lookup"><span data-stu-id="b3b25-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-171">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="b3b25-172">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-172">Description</span></span>

<span data-ttu-id="b3b25-173">Den här funktionen hämtar skrivarens ID-sträng för IEEE 1284 (inklusive längden i de två första byten i big endian-format).</span><span class="sxs-lookup"><span data-stu-id="b3b25-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-174">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-174">Parameters</span></span>

- <span data-ttu-id="b3b25-175">**skrivare**: pekar på skrivarens klass instans.</span><span class="sxs-lookup"><span data-stu-id="b3b25-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="b3b25-176">**descriptor_buffer**: pekar mot en buffert för att fylla IEEE 1284-enhets-ID-sträng (inklusive längden i de första två byte som ska formateras)</span><span class="sxs-lookup"><span data-stu-id="b3b25-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="b3b25-177">**length**: buffertens längd i byte.</span><span class="sxs-lookup"><span data-stu-id="b3b25-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-178">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-178">Return Value</span></span>

- <span data-ttu-id="b3b25-179">**UX_SUCCESS** (0x00): åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b3b25-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="b3b25-180">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="b3b25-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="b3b25-181">**UX_TRANSFER_TIMEOUT**: 0X5c-överförings-timeout, begäran slutfördes inte</span><span class="sxs-lookup"><span data-stu-id="b3b25-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="b3b25-182">**UX_TRANSFER_NOT_READY**: (0x25) enheten var i ett ogiltigt tillstånd – måste vara ansluten, adresserad eller konfigurerad.</span><span class="sxs-lookup"><span data-stu-id="b3b25-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="b3b25-183">**UX_TRANSFER_STALL**: (0X21) överföring har stoppats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="b3b25-184">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="b3b25-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="b3b25-185">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="b3b25-186">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="b3b25-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-187">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="b3b25-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="b3b25-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="b3b25-189">Läsa från ljud gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-190">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="b3b25-191">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-191">Description</span></span>

<span data-ttu-id="b3b25-192">Den här funktionen läser från ljud gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-192">This function reads from the audio interface.</span></span> <span data-ttu-id="b3b25-193">Anropet är inte blockerande.</span><span class="sxs-lookup"><span data-stu-id="b3b25-193">The call is non-blocking.</span></span> <span data-ttu-id="b3b25-194">Programmet måste se till att rätt alternativ inställning har valts för ljud strömnings gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-195">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-195">Parameters</span></span>

- <span data-ttu-id="b3b25-196">**ljud**: pekar mot klass instansen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="b3b25-197">**audio_transfer_request**: pekar mot ljud överförings strukturen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-198">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-198">Return Value</span></span>

- <span data-ttu-id="b3b25-199">**UX_SUCCESS**: (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="b3b25-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="b3b25-200">**UX_FUNCTION_NOT_SUPPORTED**"(0x54)-funktionen stöds inte</span><span class="sxs-lookup"><span data-stu-id="b3b25-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-201">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="b3b25-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="b3b25-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="b3b25-203">Skriv till ljud gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-204">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="b3b25-205">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-205">Description</span></span>

<span data-ttu-id="b3b25-206">Den här funktionen skriver till ljud gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-206">This function writes to the audio interface.</span></span> <span data-ttu-id="b3b25-207">Anropet är inte blockerande.</span><span class="sxs-lookup"><span data-stu-id="b3b25-207">The call is non-blocking.</span></span> <span data-ttu-id="b3b25-208">Programmet måste se till att rätt alternativ inställning har valts för ljud strömnings gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-209">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-209">Parameters</span></span>

- <span data-ttu-id="b3b25-210">**ljud**: pekar mot klassen Audio-klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="b3b25-211">**audio_transfer_request**: pekar mot ljud överförings strukturen</span><span class="sxs-lookup"><span data-stu-id="b3b25-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-212">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-212">Return Value</span></span>

- <span data-ttu-id="b3b25-213">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte.</span><span class="sxs-lookup"><span data-stu-id="b3b25-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="b3b25-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) gränssnitt är felaktigt.</span><span class="sxs-lookup"><span data-stu-id="b3b25-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-216">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="b3b25-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="b3b25-218">Hämta en speciell kontroll från ljud kontroll gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-219">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="b3b25-220">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-220">Description</span></span>

<span data-ttu-id="b3b25-221">Den här funktionen läser en speciell kontroll från ljud kontroll gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-222">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-222">Parameters</span></span>

- <span data-ttu-id="b3b25-223">**ljud**: pekar mot klassen Audio-klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="b3b25-224">**audio_control**: pekar mot ljud kontroll strukturen</span><span class="sxs-lookup"><span data-stu-id="b3b25-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-225">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-225">Return Value</span></span>

- <span data-ttu-id="b3b25-226">**UX_SUCCESS**: (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="b3b25-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="b3b25-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte</span><span class="sxs-lookup"><span data-stu-id="b3b25-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="b3b25-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="b3b25-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-229">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="b3b25-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="b3b25-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="b3b25-231">Ange en speciell kontroll för ljud kontroll gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-232">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="b3b25-233">\* \* Beskrivning \* \*</span><span class="sxs-lookup"><span data-stu-id="b3b25-233">\*\*Description \*\*</span></span>

<span data-ttu-id="b3b25-234">Den här funktionen anger en speciell kontroll för ljud kontroll gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-235">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-235">Parameters</span></span>

- <span data-ttu-id="b3b25-236">**ljud**: pekar mot klassen Audio-klass</span><span class="sxs-lookup"><span data-stu-id="b3b25-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="b3b25-237">**audio_control**: pekar mot ljud kontroll strukturen</span><span class="sxs-lookup"><span data-stu-id="b3b25-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-238">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-238">Return Value</span></span>

- <span data-ttu-id="b3b25-239">**UX_SUCCESS**: (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="b3b25-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="b3b25-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte</span><span class="sxs-lookup"><span data-stu-id="b3b25-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="b3b25-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="b3b25-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-242">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="b3b25-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="b3b25-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="b3b25-244">Ange ett alternativt inställnings gränssnitt för ljud strömnings gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-245">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="b3b25-246">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-246">Description</span></span>

<span data-ttu-id="b3b25-247">Den här funktionen ställer in rätt alternativ gränssnitt för ljud strömnings gränssnittet enligt en speciell samplings struktur.</span><span class="sxs-lookup"><span data-stu-id="b3b25-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-248">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-248">Parameters</span></span>

- <span data-ttu-id="b3b25-249">**ljud**: pekar mot klass instansen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="b3b25-250">**audio_sampling**: pekar mot ljud samplings strukturen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-251">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-251">Return Value</span></span>

- <span data-ttu-id="b3b25-252">**UX_SUCCESS**: (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="b3b25-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="b3b25-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte</span><span class="sxs-lookup"><span data-stu-id="b3b25-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="b3b25-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="b3b25-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="b3b25-255">**UX_NO_ALTERNATE_SETTING**: (0X5e) ingen alternativ inställning för samplings värden</span><span class="sxs-lookup"><span data-stu-id="b3b25-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-256">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="b3b25-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="b3b25-258">Hämta möjliga samplings inställningar för ljud strömnings gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="b3b25-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-259">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="b3b25-260">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-260">Description</span></span>

<span data-ttu-id="b3b25-261">Den här funktionen hämtar, en i taget, alla möjliga samplings inställningar som är tillgängliga i de olika alternativen för ljud strömnings gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="b3b25-262">Första gången funktionen används måste alla fält i den anropande struktur pekaren återställas.</span><span class="sxs-lookup"><span data-stu-id="b3b25-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="b3b25-263">Funktionen returnerar en speciell uppsättning strömmande värden vid RETUR om inte slutet på de alternativa inställningarna har uppnåtts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="b3b25-264">När den här funktionen återanvänds, kommer de tidigare samplings värdena att användas för att hitta nästa samplings värde.</span><span class="sxs-lookup"><span data-stu-id="b3b25-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-265">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-265">Parameters</span></span>

- <span data-ttu-id="b3b25-266">**ljud**: pekar mot klass instansen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="b3b25-267">**audio_sampling**: pekar mot ljud samplings strukturen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-268">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-268">Return Value</span></span>

- <span data-ttu-id="b3b25-269">**UX_SUCCESS**: (0x00) data överföringen har slutförts</span><span class="sxs-lookup"><span data-stu-id="b3b25-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="b3b25-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte</span><span class="sxs-lookup"><span data-stu-id="b3b25-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="b3b25-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt</span><span class="sxs-lookup"><span data-stu-id="b3b25-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="b3b25-272">**UX_NO_ALTERNATE_SETTING**: (0X5e) ingen alternativ inställning för samplings värden</span><span class="sxs-lookup"><span data-stu-id="b3b25-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-273">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="b3b25-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="b3b25-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="b3b25-275">Läsa från asix-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-276">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-277">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-277">Description</span></span>

<span data-ttu-id="b3b25-278">Den här funktionen läser från asix-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-278">This function reads from the asix interface.</span></span> <span data-ttu-id="b3b25-279">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="b3b25-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-280">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-280">Parameters</span></span>

- <span data-ttu-id="b3b25-281">**asix**: pekar mot instans av asix-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="b3b25-282">**data_pointer**: pekar mot buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="b3b25-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="b3b25-283">**requested_length**: längden som ska tas emot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="b3b25-284">**actual_length**: den längd som faktiskt mottagits.</span><span class="sxs-lookup"><span data-stu-id="b3b25-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-285">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-285">Return Value</span></span>

- <span data-ttu-id="b3b25-286">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-287">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, Läsning ofullständig.</span><span class="sxs-lookup"><span data-stu-id="b3b25-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-288">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="b3b25-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="b3b25-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="b3b25-290">Skriv till asix-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-291">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="b3b25-292">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-292">Description</span></span>

<span data-ttu-id="b3b25-293">Den här funktionen skriver till asix-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-293">This function writes to the asix interface.</span></span> <span data-ttu-id="b3b25-294">Anropet är inte blockerat.</span><span class="sxs-lookup"><span data-stu-id="b3b25-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-295">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-295">Parameters</span></span>

- <span data-ttu-id="b3b25-296">**asix**: pekar mot instans av asix-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="b3b25-297">**paket**: netx-datapaket</span><span class="sxs-lookup"><span data-stu-id="b3b25-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-298">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-298">Return Value</span></span>

- <span data-ttu-id="b3b25-299">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-300">**UX_ERROR**: (0xFF) Det gick inte att begära överföring.</span><span class="sxs-lookup"><span data-stu-id="b3b25-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-301">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="b3b25-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="b3b25-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="b3b25-303">Öppna en session mellan initierare och svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-304">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="b3b25-305">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-305">Description</span></span>

<span data-ttu-id="b3b25-306">Den här funktionen öppnar en session mellan en PIMA-initierare och en PIMA-svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="b3b25-307">När en session har öppnats kan de flesta PIMA-kommandon köras.</span><span class="sxs-lookup"><span data-stu-id="b3b25-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-308">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-308">Parameters</span></span>

- <span data-ttu-id="b3b25-309">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-310">**pima_sessio**: pekare till pima session<</span><span class="sxs-lookup"><span data-stu-id="b3b25-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-311">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-311">Return Value</span></span>

- <span data-ttu-id="b3b25-312">**UX_SUCCESS**: (0X00) session har öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="b3b25-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E)-sessionen är redan öppen</span><span class="sxs-lookup"><span data-stu-id="b3b25-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-314">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="b3b25-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="b3b25-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="b3b25-316">Stäng en session mellan initierare och svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-317">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="b3b25-318">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-318">Description</span></span>

<span data-ttu-id="b3b25-319">Den här funktionen stänger en session som tidigare har öppnats mellan en PIMA-initierare och en PIMA-svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="b3b25-320">När en session har stängts går det inte längre att köra de flesta PIMA-kommandon.</span><span class="sxs-lookup"><span data-stu-id="b3b25-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-321">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-321">Parameters</span></span>

- <span data-ttu-id="b3b25-322">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-323">**pima_session**: pekare till Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-324">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-324">Return Value</span></span>

- <span data-ttu-id="b3b25-325">**UX_SUCCESS**: (0x00) sessionen stängdes.</span><span class="sxs-lookup"><span data-stu-id="b3b25-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="b3b25-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-327">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="b3b25-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="b3b25-329">Hämta lagrings-ID-matrisen från svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-330">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-331">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-331">Description</span></span>

<span data-ttu-id="b3b25-332">Den här funktionen hämtar lagrings-ID-matrisen från svararen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-333">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-333">Parameters</span></span>

- <span data-ttu-id="b3b25-334">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-335">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-336">**storage_ids_array**: matris där lagrings-ID: n ska returneras</span><span class="sxs-lookup"><span data-stu-id="b3b25-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="b3b25-337">**storage_id_length**: lagrings mat ris längden</span><span class="sxs-lookup"><span data-stu-id="b3b25-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-338">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-338">Return Value</span></span>

- <span data-ttu-id="b3b25-339">**UX_SUCCESS**: (0x00) matrisen med LAGRINGS-ID har fyllts i</span><span class="sxs-lookup"><span data-stu-id="b3b25-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="b3b25-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-341">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-342">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="b3b25-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="b3b25-344">Hämta lagrings informationen från svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-345">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="b3b25-346">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-346">Description</span></span>

<span data-ttu-id="b3b25-347">Den här funktionen hämtar lagrings informationen för en lagrings behållare med värde *storage_id*.</span><span class="sxs-lookup"><span data-stu-id="b3b25-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-348">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-348">Parameters</span></span>

- <span data-ttu-id="b3b25-349">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-350">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-351">**storage_id**: ID för lagrings containern</span><span class="sxs-lookup"><span data-stu-id="b3b25-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="b3b25-352">**lagring**: pekare till Storage information container</span><span class="sxs-lookup"><span data-stu-id="b3b25-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-353">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-353">Return Value</span></span>

- <span data-ttu-id="b3b25-354">**UX_SUCCESS**: (0x00) lagrings informationen hämtades</span><span class="sxs-lookup"><span data-stu-id="b3b25-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="b3b25-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-356">**UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-357">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="b3b25-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="b3b25-359">Hämta antalet objekt på en lagrings behållare från svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-360">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="b3b25-361">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-361">Description</span></span>

<span data-ttu-id="b3b25-362">Den här funktionen hämtar antalet objekt som lagras på en angiven lagrings behållare med värde storage_id som matchar en speciell format kod.</span><span class="sxs-lookup"><span data-stu-id="b3b25-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="b3b25-363">Antalet objekt returneras i fältet: ux_host_class_pima_session_nb_objects i pima_sessions strukturen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-364">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-364">Parameters</span></span>

- <span data-ttu-id="b3b25-365">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-366">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-367">**storage_id**: ID för lagrings containern</span><span class="sxs-lookup"><span data-stu-id="b3b25-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="b3b25-368">**object_format_code**: objekt format kod filter.</span><span class="sxs-lookup"><span data-stu-id="b3b25-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="b3b25-369">Objekt format koderna kan ha ett av följande värden.</span><span class="sxs-lookup"><span data-stu-id="b3b25-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="b3b25-370">Objekt format kod</span><span class="sxs-lookup"><span data-stu-id="b3b25-370">Object Format Code</span></span>               | <span data-ttu-id="b3b25-371">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-371">Description</span></span>   |     <span data-ttu-id="b3b25-372">USBX-kod</span><span class="sxs-lookup"><span data-stu-id="b3b25-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="b3b25-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="b3b25-373">0x3000</span></span>                           | <span data-ttu-id="b3b25-374">Odefinierat odefinierade icke-avbildnings objekt</span><span class="sxs-lookup"><span data-stu-id="b3b25-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="b3b25-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="b3b25-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="b3b25-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="b3b25-376">0x3001</span></span>                           | <span data-ttu-id="b3b25-377">Associerings Association (t. ex. mapp)</span><span class="sxs-lookup"><span data-stu-id="b3b25-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="b3b25-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="b3b25-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="b3b25-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="b3b25-379">0x3002</span></span>                           | <span data-ttu-id="b3b25-380">Skript enhet-modell för skript</span><span class="sxs-lookup"><span data-stu-id="b3b25-380">Script Device-model specific script</span></span> | <span data-ttu-id="b3b25-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="b3b25-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="b3b25-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="b3b25-382">0x3003</span></span>                           | <span data-ttu-id="b3b25-383">Körbar enhets modell – en unik binär körbar fil</span><span class="sxs-lookup"><span data-stu-id="b3b25-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="b3b25-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="b3b25-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="b3b25-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="b3b25-385">0x3004</span></span>                           | <span data-ttu-id="b3b25-386">Text text fil</span><span class="sxs-lookup"><span data-stu-id="b3b25-386">Text Text file</span></span>  |   <span data-ttu-id="b3b25-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="b3b25-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="b3b25-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="b3b25-388">0x3005</span></span>                           | <span data-ttu-id="b3b25-389">HTML HyperText Markup Language-fil (text)</span><span class="sxs-lookup"><span data-stu-id="b3b25-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="b3b25-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="b3b25-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="b3b25-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="b3b25-391">0x3006</span></span>                           | <span data-ttu-id="b3b25-392">DPOF Digital utskrifts order format fil (text)</span><span class="sxs-lookup"><span data-stu-id="b3b25-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="b3b25-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="b3b25-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="b3b25-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="b3b25-394">0x3007</span></span>                           | <span data-ttu-id="b3b25-395">AIFF-ljudklipp</span><span class="sxs-lookup"><span data-stu-id="b3b25-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="b3b25-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="b3b25-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="b3b25-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="b3b25-397">0x3008</span></span>                           | <span data-ttu-id="b3b25-398">WAV-ljud klipp</span><span class="sxs-lookup"><span data-stu-id="b3b25-398">WAV Audio clip</span></span>   |  <span data-ttu-id="b3b25-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="b3b25-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="b3b25-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="b3b25-400">0x3009</span></span>                           | <span data-ttu-id="b3b25-401">MP3-ljud klipp</span><span class="sxs-lookup"><span data-stu-id="b3b25-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="b3b25-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="b3b25-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="b3b25-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="b3b25-403">0x300A</span></span>                           | <span data-ttu-id="b3b25-404">AVI-videoklipp</span><span class="sxs-lookup"><span data-stu-id="b3b25-404">AVI Video clip</span></span>   |  <span data-ttu-id="b3b25-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="b3b25-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="b3b25-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="b3b25-406">0x300B</span></span>                           | <span data-ttu-id="b3b25-407">MPEG-videoklipp</span><span class="sxs-lookup"><span data-stu-id="b3b25-407">MPEG Video clip</span></span>  |  <span data-ttu-id="b3b25-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="b3b25-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="b3b25-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="b3b25-409">0x300C</span></span>                           | <span data-ttu-id="b3b25-410">ASF Microsoft Advanced Streaming format (video)</span><span class="sxs-lookup"><span data-stu-id="b3b25-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="b3b25-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="b3b25-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="b3b25-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="b3b25-412">0x3800</span></span>                           | <span data-ttu-id="b3b25-413">Odefinierat okänt bild objekt</span><span class="sxs-lookup"><span data-stu-id="b3b25-413">Undefined Unknown image object</span></span> | <span data-ttu-id="b3b25-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="b3b25-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="b3b25-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="b3b25-415">0x3801</span></span>                           | <span data-ttu-id="b3b25-416">EXIF/JPEG-utbytbart fil format, JEIDA standard</span><span class="sxs-lookup"><span data-stu-id="b3b25-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="b3b25-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="b3b25-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="b3b25-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="b3b25-418">0x3802</span></span>                           | <span data-ttu-id="b3b25-419">TIFF/EP tag Image File Format för elektronisk fotografering</span><span class="sxs-lookup"><span data-stu-id="b3b25-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="b3b25-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="b3b25-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="b3b25-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="b3b25-421">0x3803</span></span>                           | <span data-ttu-id="b3b25-422">Bild format för FlashPix-strukturerad lagring</span><span class="sxs-lookup"><span data-stu-id="b3b25-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="b3b25-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="b3b25-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="b3b25-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="b3b25-424">0x3804</span></span>                           | <span data-ttu-id="b3b25-425">BMP Microsoft Windows-bitmappsfil</span><span class="sxs-lookup"><span data-stu-id="b3b25-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="b3b25-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="b3b25-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="b3b25-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="b3b25-427">0x3805</span></span>                           | <span data-ttu-id="b3b25-428">CIFF Canon Camera Image File Format</span><span class="sxs-lookup"><span data-stu-id="b3b25-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="b3b25-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="b3b25-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="b3b25-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="b3b25-430">0x3806</span></span>                           | <span data-ttu-id="b3b25-431">Odefinierad reserverad</span><span class="sxs-lookup"><span data-stu-id="b3b25-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="b3b25-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="b3b25-432">0x3807</span></span>                           | <span data-ttu-id="b3b25-433">GIF-Graphics Interchange Format</span><span class="sxs-lookup"><span data-stu-id="b3b25-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="b3b25-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="b3b25-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="b3b25-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="b3b25-435">0x3808</span></span>                           | <span data-ttu-id="b3b25-436">JFIF JPEG File Interchange Format</span><span class="sxs-lookup"><span data-stu-id="b3b25-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="b3b25-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="b3b25-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="b3b25-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="b3b25-438">0x3809</span></span>                           | <span data-ttu-id="b3b25-439">PCD PhotoCD-avbildning PAC</span><span class="sxs-lookup"><span data-stu-id="b3b25-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="b3b25-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="b3b25-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="b3b25-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="b3b25-441">0x380A</span></span>                           | <span data-ttu-id="b3b25-442">PICT QuickDraw bild format</span><span class="sxs-lookup"><span data-stu-id="b3b25-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="b3b25-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="b3b25-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="b3b25-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="b3b25-444">0x380B</span></span>                           | <span data-ttu-id="b3b25-445">PNG-Portable Network Graphics</span><span class="sxs-lookup"><span data-stu-id="b3b25-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="b3b25-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="b3b25-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="b3b25-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="b3b25-447">0x380C</span></span>                           | <span data-ttu-id="b3b25-448">Odefinierad reserverad</span><span class="sxs-lookup"><span data-stu-id="b3b25-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="b3b25-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="b3b25-449">0x380D</span></span>                           | <span data-ttu-id="b3b25-450">TIFF-tagg bild fil format</span><span class="sxs-lookup"><span data-stu-id="b3b25-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="b3b25-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="b3b25-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="b3b25-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="b3b25-452">0x380E</span></span>                           | <span data-ttu-id="b3b25-453">TIFF/IT-tagga bild fil format för informations teknik (grafik)</span><span class="sxs-lookup"><span data-stu-id="b3b25-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="b3b25-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="b3b25-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="b3b25-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="b3b25-455">0x380F</span></span>                           | <span data-ttu-id="b3b25-456">JP2 JPEG2000-format för original fil</span><span class="sxs-lookup"><span data-stu-id="b3b25-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="b3b25-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="b3b25-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="b3b25-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="b3b25-458">0x3810</span></span>                           | <span data-ttu-id="b3b25-459">JPX JPEG2000-utökat fil format</span><span class="sxs-lookup"><span data-stu-id="b3b25-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="b3b25-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="b3b25-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="b3b25-461">Alla andra koder med MSN 0011</span><span class="sxs-lookup"><span data-stu-id="b3b25-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="b3b25-462">Alla odefinierade reserverade för framtida användning</span><span class="sxs-lookup"><span data-stu-id="b3b25-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="b3b25-463">Alla övriga koder med MSN på 1011</span><span class="sxs-lookup"><span data-stu-id="b3b25-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="b3b25-464">En leverantörsdefinierade typ som har angetts av leverantören: avbildning</span><span class="sxs-lookup"><span data-stu-id="b3b25-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="b3b25-465">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-465">Return Value</span></span>

- <span data-ttu-id="b3b25-466">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-468">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-469">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="b3b25-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="b3b25-471">Hämta objekt referenser från svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-472">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="b3b25-473">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-473">Description</span></span>

<span data-ttu-id="b3b25-474">Returnerar en matris med objekt referenser som finns i den lagrings behållare som anges av parametern storage_id.</span><span class="sxs-lookup"><span data-stu-id="b3b25-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="b3b25-475">Om en sammanställd lista över alla butiker önskas, anges värdet 0xFFFFFFFF för värdet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-476">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-476">Parameters</span></span>

- <span data-ttu-id="b3b25-477">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-478">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-479">**object_handes_array**: matris där referenser returneras</span><span class="sxs-lookup"><span data-stu-id="b3b25-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="b3b25-480">**object_handles_length**: matrisens längd</span><span class="sxs-lookup"><span data-stu-id="b3b25-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="b3b25-481">**storage_id**: ID för lagrings containern</span><span class="sxs-lookup"><span data-stu-id="b3b25-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="b3b25-482">**object_format_code**: formatera kod för objekt (se tabell för funktionen ux_host_class_pima_num_objects_get)</span><span class="sxs-lookup"><span data-stu-id="b3b25-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="b3b25-483">**object_handle_association**: valfritt objekt kopplings värde</span><span class="sxs-lookup"><span data-stu-id="b3b25-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="b3b25-484">Objekt referens associationen kan vara något av värdet från tabellen nedan:</span><span class="sxs-lookup"><span data-stu-id="b3b25-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="b3b25-485">AssociationCode</span><span class="sxs-lookup"><span data-stu-id="b3b25-485">AssociationCode</span></span>                        | <span data-ttu-id="b3b25-486">AssociationType</span><span class="sxs-lookup"><span data-stu-id="b3b25-486">AssociationType</span></span>      | <span data-ttu-id="b3b25-487">Tolkning</span><span class="sxs-lookup"><span data-stu-id="b3b25-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="b3b25-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="b3b25-488">0x0000</span></span>                                 | <span data-ttu-id="b3b25-489">Undefined (Odefinierad)</span><span class="sxs-lookup"><span data-stu-id="b3b25-489">Undefined</span></span>            | <span data-ttu-id="b3b25-490">Undefined (Odefinierad)</span><span class="sxs-lookup"><span data-stu-id="b3b25-490">Undefined</span></span>            |
| <span data-ttu-id="b3b25-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="b3b25-491">0x0001</span></span>                                 | <span data-ttu-id="b3b25-492">GenericFolder</span><span class="sxs-lookup"><span data-stu-id="b3b25-492">GenericFolder</span></span>        | <span data-ttu-id="b3b25-493">Outnyttja</span><span class="sxs-lookup"><span data-stu-id="b3b25-493">Unused</span></span>               |
| <span data-ttu-id="b3b25-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="b3b25-494">0x0002</span></span>                                 | <span data-ttu-id="b3b25-495">Artist</span><span class="sxs-lookup"><span data-stu-id="b3b25-495">Album</span></span>                | <span data-ttu-id="b3b25-496">Reserverat</span><span class="sxs-lookup"><span data-stu-id="b3b25-496">Reserved</span></span>             |
| <span data-ttu-id="b3b25-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="b3b25-497">0x0003</span></span>                                 | <span data-ttu-id="b3b25-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="b3b25-498">TimeSequence</span></span>         | <span data-ttu-id="b3b25-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="b3b25-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="b3b25-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="b3b25-500">0x0004</span></span>                                 | <span data-ttu-id="b3b25-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="b3b25-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="b3b25-502">Outnyttja</span><span class="sxs-lookup"><span data-stu-id="b3b25-502">Unused</span></span>               |
| <span data-ttu-id="b3b25-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="b3b25-503">0x0005</span></span>                                 | <span data-ttu-id="b3b25-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="b3b25-504">VerticalPanoramic</span></span>    | <span data-ttu-id="b3b25-505">Outnyttja</span><span class="sxs-lookup"><span data-stu-id="b3b25-505">Unused</span></span>               |
| <span data-ttu-id="b3b25-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="b3b25-506">0x0006</span></span>                                 | <span data-ttu-id="b3b25-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="b3b25-507">2DPanoramic</span></span>          | <span data-ttu-id="b3b25-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="b3b25-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="b3b25-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="b3b25-509">0x0007</span></span>                                 | <span data-ttu-id="b3b25-510">AncillaryData</span><span class="sxs-lookup"><span data-stu-id="b3b25-510">AncillaryData</span></span>        | <span data-ttu-id="b3b25-511">Undefined (Odefinierad)</span><span class="sxs-lookup"><span data-stu-id="b3b25-511">Undefined</span></span>            |
| <span data-ttu-id="b3b25-512">Alla andra värden med bit 15 inställt på 0</span><span class="sxs-lookup"><span data-stu-id="b3b25-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="b3b25-513">Reserverat</span><span class="sxs-lookup"><span data-stu-id="b3b25-513">Reserved</span></span>             | <span data-ttu-id="b3b25-514">Undefined (Odefinierad)</span><span class="sxs-lookup"><span data-stu-id="b3b25-514">Undefined</span></span>            |
| <span data-ttu-id="b3b25-515">Alla värden med bit 15 inställt på 1</span><span class="sxs-lookup"><span data-stu-id="b3b25-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="b3b25-516">Leverantörsdefinierade</span><span class="sxs-lookup"><span data-stu-id="b3b25-516">Vendor-Defined</span></span>       | <span data-ttu-id="b3b25-517">Leverantörsdefinierade</span><span class="sxs-lookup"><span data-stu-id="b3b25-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="b3b25-518">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-518">Return Value</span></span>

- <span data-ttu-id="b3b25-519">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-521">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-522">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="b3b25-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="b3b25-524">Hämta objekt informationen från svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-525">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="b3b25-526">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-526">Description</span></span>

<span data-ttu-id="b3b25-527">Den här funktionen hämtar objekt information för en objekt referens.</span><span class="sxs-lookup"><span data-stu-id="b3b25-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-528">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-528">Parameters</span></span>

- <span data-ttu-id="b3b25-529">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-530">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-531">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b3b25-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="b3b25-532">**objekt**: pekare till objekt information container</span><span class="sxs-lookup"><span data-stu-id="b3b25-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-533">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-533">Return Value</span></span>

- <span data-ttu-id="b3b25-534">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-536">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-537">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="b3b25-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="b3b25-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="b3b25-539">Skicka objekt informationen till responder.</span><span class="sxs-lookup"><span data-stu-id="b3b25-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-540">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="b3b25-541">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-541">Description</span></span>

<span data-ttu-id="b3b25-542">Den här funktionen skickar lagrings informationen för en lagrings behållare med värde storage_id.</span><span class="sxs-lookup"><span data-stu-id="b3b25-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="b3b25-543">Initieraren bör använda det här kommandot innan du skickar ett objekt till den svarande.</span><span class="sxs-lookup"><span data-stu-id="b3b25-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-544">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-544">Parameters</span></span>

- <span data-ttu-id="b3b25-545">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-546">**pima_session**: pekare till Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="b3b25-547">**storage_id**: mål LAGRINGS-ID.</span><span class="sxs-lookup"><span data-stu-id="b3b25-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="b3b25-548">**parent_object_id**: överordnad ObjectHandle i svarare där objektet ska placeras.</span><span class="sxs-lookup"><span data-stu-id="b3b25-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="b3b25-549">**objekt**: pekar mot objekt informations behållare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-550">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-550">Return Value</span></span>

- <span data-ttu-id="b3b25-551">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-553">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-554">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="b3b25-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="b3b25-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="b3b25-556">Öppna ett objekt som lagras i svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-557">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="b3b25-558">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-558">Description</span></span>

<span data-ttu-id="b3b25-559">Den här funktionen öppnar ett objekt på den svarande innan den läses eller skrivs.</span><span class="sxs-lookup"><span data-stu-id="b3b25-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-560">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-560">Parameters</span></span>

- <span data-ttu-id="b3b25-561">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-562">**pima_session**: pekare till Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="b3b25-563">**object_handle**: objektets handtag.</span><span class="sxs-lookup"><span data-stu-id="b3b25-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="b3b25-564">**objec**: pekar mot objekt informations behållare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-565">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-565">Return Value</span></span>

- <span data-ttu-id="b3b25-566">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021)-objektet har redan öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="b3b25-569">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-570">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="b3b25-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="b3b25-572">Hämta ett objekt som lagras i svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-573">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-574">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-574">Description</span></span>

<span data-ttu-id="b3b25-575">Den här funktionen hämtar ett objekt på den svarande.</span><span class="sxs-lookup"><span data-stu-id="b3b25-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-576">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-576">Parameters</span></span>

- <span data-ttu-id="b3b25-577">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-578">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-579">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b3b25-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="b3b25-580">**objekt**: pekare till objekt information container</span><span class="sxs-lookup"><span data-stu-id="b3b25-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="b3b25-581">**object_buffer**: adress för objekt data</span><span class="sxs-lookup"><span data-stu-id="b3b25-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="b3b25-582">**object_buffer_length**: begärd objekt längd</span><span class="sxs-lookup"><span data-stu-id="b3b25-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="b3b25-583">**object_actual_length**: den returnerade objekt längden</span><span class="sxs-lookup"><span data-stu-id="b3b25-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-584">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-584">Return Value</span></span>

- <span data-ttu-id="b3b25-585">**UX_SUCCESS**: (0x00) objektet överfördes</span><span class="sxs-lookup"><span data-stu-id="b3b25-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="b3b25-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="b3b25-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) åtkomst till objekt nekad</span><span class="sxs-lookup"><span data-stu-id="b3b25-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="b3b25-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) överföring är ofullständig</span><span class="sxs-lookup"><span data-stu-id="b3b25-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="b3b25-590">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="b3b25-591">**UX_TRANSFER_ERROR**: (0X23) överförings fel vid läsning av objekt</span><span class="sxs-lookup"><span data-stu-id="b3b25-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-592">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="b3b25-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="b3b25-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="b3b25-594">Skicka ett objekt som lagras i svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-595">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-596">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-596">Description</span></span>

<span data-ttu-id="b3b25-597">Den här funktionen skickar ett objekt till responder.</span><span class="sxs-lookup"><span data-stu-id="b3b25-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-598">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-598">Parameters</span></span>

- <span data-ttu-id="b3b25-599">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-600">**pima_sessio**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-601">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b3b25-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="b3b25-602">**objekt**: pekare till objekt information container</span><span class="sxs-lookup"><span data-stu-id="b3b25-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="b3b25-603">**object_buffer**: adress för objekt data</span><span class="sxs-lookup"><span data-stu-id="b3b25-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="b3b25-604">**object_buffer_length**: begärd objekt längd</span><span class="sxs-lookup"><span data-stu-id="b3b25-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-605">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-605">Return Value</span></span>

- <span data-ttu-id="b3b25-606">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats</span><span class="sxs-lookup"><span data-stu-id="b3b25-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="b3b25-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="b3b25-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) åtkomst till objekt nekad</span><span class="sxs-lookup"><span data-stu-id="b3b25-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="b3b25-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) överföring är ofullständig</span><span class="sxs-lookup"><span data-stu-id="b3b25-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="b3b25-611">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="b3b25-612">**UX_TRANSFER_ERROR**: (0X23) överförings fel vid skrivning av objekt</span><span class="sxs-lookup"><span data-stu-id="b3b25-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-613">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="b3b25-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="b3b25-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="b3b25-615">Hämta ett tumm-objekt som lagras i svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-616">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-617">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-617">Description</span></span>

<span data-ttu-id="b3b25-618">Den här funktionen hämtar ett tumme-objekt på den svarande.</span><span class="sxs-lookup"><span data-stu-id="b3b25-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-619">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-619">Parameters</span></span>

- <span data-ttu-id="b3b25-620">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-621">**pima_session**: pekare till Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="b3b25-622">**object_handle**: objektets handtag.</span><span class="sxs-lookup"><span data-stu-id="b3b25-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="b3b25-623">**objekt**: pekar mot objekt informations behållare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="b3b25-624">**thumb_buffer**: adress för objekt data för tummen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="b3b25-625">**thumb_buffer_length**: den begärda längden för tumm-objektet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="b3b25-626">**thumb_actual_length**: längden på det returnerade objektet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-627">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-627">Return Value</span></span>

- <span data-ttu-id="b3b25-628">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="b3b25-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="b3b25-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) åtkomst till objekt nekad.</span><span class="sxs-lookup"><span data-stu-id="b3b25-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="b3b25-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) överföring är ofullständig.</span><span class="sxs-lookup"><span data-stu-id="b3b25-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="b3b25-633">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="b3b25-634">**UX_TRANSFER_ERROR**: (0X23) överförings fel vid läsning av objekt.</span><span class="sxs-lookup"><span data-stu-id="b3b25-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-635">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="b3b25-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="b3b25-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="b3b25-637">Ta bort ett objekt som lagras i svarare.</span><span class="sxs-lookup"><span data-stu-id="b3b25-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-638">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="b3b25-639">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-639">Description</span></span>

<span data-ttu-id="b3b25-640">Den här funktionen tar bort ett objekt på den svarande</span><span class="sxs-lookup"><span data-stu-id="b3b25-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-641">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-641">Parameters</span></span>

- <span data-ttu-id="b3b25-642">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-643">**pima_session**: pekare till Pima-session</span><span class="sxs-lookup"><span data-stu-id="b3b25-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="b3b25-644">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b3b25-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-645">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-645">Return Value</span></span>

- <span data-ttu-id="b3b25-646">**UX_SUCCESS**: (0x00) objektet har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="b3b25-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="b3b25-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="b3b25-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) Det går inte att ta bort objekt.</span><span class="sxs-lookup"><span data-stu-id="b3b25-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="b3b25-649">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-650">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="b3b25-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="b3b25-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="b3b25-652">Stäng ett objekt som lagras i svars listan</span><span class="sxs-lookup"><span data-stu-id="b3b25-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="b3b25-654">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-654">Description</span></span>

<span data-ttu-id="b3b25-655">Den här funktionen stänger ett objekt på den svarande.</span><span class="sxs-lookup"><span data-stu-id="b3b25-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-656">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-656">Parameters</span></span>

- <span data-ttu-id="b3b25-657">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b3b25-658">**pima_session**: pekare till Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="b3b25-659">**object_handle**: objektets handtag.</span><span class="sxs-lookup"><span data-stu-id="b3b25-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="b3b25-660">**objekt**: pekar mot objekt.</span><span class="sxs-lookup"><span data-stu-id="b3b25-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-661">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-661">Return Value</span></span>

- <span data-ttu-id="b3b25-662">**UX_SUCCESS**: (0x00) objektet stängdes.</span><span class="sxs-lookup"><span data-stu-id="b3b25-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="b3b25-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="b3b25-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="b3b25-665">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-666">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="b3b25-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="b3b25-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="b3b25-668">Läsa från det allmänna seriella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-669">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-670">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-670">Description</span></span>

<span data-ttu-id="b3b25-671">Den här funktionen läser från det allmänna serie gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="b3b25-672">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="b3b25-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-673">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-673">Parameters</span></span>

- <span data-ttu-id="b3b25-674">**gser**: pekar mot instans av gser-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="b3b25-675">**interface_index**: gränssnitts index som ska läsas från.</span><span class="sxs-lookup"><span data-stu-id="b3b25-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="b3b25-676">**data_pointer**: pekar mot buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="b3b25-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="b3b25-677">**requested_length**: längden som ska tas emot.</span><span class="sxs-lookup"><span data-stu-id="b3b25-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="b3b25-678">**actual_length**: den längd som faktiskt mottagits.</span><span class="sxs-lookup"><span data-stu-id="b3b25-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-679">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-679">Return Value</span></span>

- <span data-ttu-id="b3b25-680">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-681">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, Läsning ofullständig.</span><span class="sxs-lookup"><span data-stu-id="b3b25-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-682">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="b3b25-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="b3b25-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="b3b25-684">Skriv till det allmänna seriella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-685">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="b3b25-686">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-686">Description</span></span>

<span data-ttu-id="b3b25-687">Den här funktionen skriver till det allmänna serie gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="b3b25-688">Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="b3b25-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-689">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-689">Parameters</span></span>

- <span data-ttu-id="b3b25-690">**gser**: pekar mot instans av gser-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="b3b25-691">**interface_index**: gränssnittet som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="b3b25-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="b3b25-692">**data_pointer**: pekar mot buffertstorleken för data nytto lasten.</span><span class="sxs-lookup"><span data-stu-id="b3b25-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="b3b25-693">**requested_length**: längden som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="b3b25-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="b3b25-694">**actual_length**: den längd som faktiskt har skickats.</span><span class="sxs-lookup"><span data-stu-id="b3b25-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-695">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-695">Return Value</span></span>

- <span data-ttu-id="b3b25-696">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-697">**UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, skrivning ofullständig.</span><span class="sxs-lookup"><span data-stu-id="b3b25-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-698">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="b3b25-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="b3b25-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="b3b25-700">Utföra en IOCTL-funktion på det allmänna seriella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-701">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="b3b25-702">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-702">Description</span></span>

<span data-ttu-id="b3b25-703">Den här funktionen utför en angiven IOCTL-funktion till gser-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="b3b25-704">Anropet blockeras och returneras bara när det uppstår ett fel eller när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-705">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-705">Parameters</span></span>

- <span data-ttu-id="b3b25-706">**gser**: pekar mot instans av gser-klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="b3b25-707">**ioctl_function**: IOCTL-funktion som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="b3b25-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="b3b25-708">Se tabellen nedan för en av de tillåtna IOCTL-funktionerna.</span><span class="sxs-lookup"><span data-stu-id="b3b25-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="b3b25-709">**parameter**: Pointerto en parameter som är unik för IOCTL</span><span class="sxs-lookup"><span data-stu-id="b3b25-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-710">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-710">Return Value</span></span>

- <span data-ttu-id="b3b25-711">**UX_SUCCESS**: (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-712">**UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne.</span><span class="sxs-lookup"><span data-stu-id="b3b25-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="b3b25-713">**UX_HOST_CLASS_UNKNOWN**: (0X59) fel klass instans</span><span class="sxs-lookup"><span data-stu-id="b3b25-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="b3b25-714">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) Okänd IOCTL-funktion.</span><span class="sxs-lookup"><span data-stu-id="b3b25-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="b3b25-715">IOCTL-funktioner</span><span class="sxs-lookup"><span data-stu-id="b3b25-715">IOCTL functions</span></span>

- <span data-ttu-id="b3b25-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="b3b25-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="b3b25-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="b3b25-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="b3b25-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="b3b25-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="b3b25-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="b3b25-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="b3b25-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="b3b25-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="b3b25-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="b3b25-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="b3b25-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="b3b25-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="b3b25-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="b3b25-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-724">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="b3b25-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="b3b25-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="b3b25-726">Börja ta emot på det allmänna seriella gränssnittet</span><span class="sxs-lookup"><span data-stu-id="b3b25-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-727">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="b3b25-728">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-728">Description</span></span>

<span data-ttu-id="b3b25-729">Den här funktionen startar mottagningen på det generiska gränssnittet för seriella klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="b3b25-730">Den här funktionen tillåter icke-blockerande mottagning.</span><span class="sxs-lookup"><span data-stu-id="b3b25-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="b3b25-731">När en buffert tas emot anropas en motringning i programmet.</span><span class="sxs-lookup"><span data-stu-id="b3b25-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-732">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-732">Parameters</span></span>

- <span data-ttu-id="b3b25-733">**gser** Pekare till gser-klass instansen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="b3b25-734">**gser_reception** Struktur som innehåller mottagnings parametrarna</span><span class="sxs-lookup"><span data-stu-id="b3b25-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-735">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-735">Return Value</span></span>

- <span data-ttu-id="b3b25-736">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-737">**UX_HOST_CLASS_UNKNOWN** (0X59) fel klass instans</span><span class="sxs-lookup"><span data-stu-id="b3b25-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="b3b25-738">**UX_ERROR** (0x01)-fel</span><span class="sxs-lookup"><span data-stu-id="b3b25-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-739">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="b3b25-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="b3b25-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="b3b25-741">Sluta ta emot det allmänna seriella gränssnittet</span><span class="sxs-lookup"><span data-stu-id="b3b25-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="b3b25-742">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b3b25-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="b3b25-743">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b3b25-743">Description</span></span>

<span data-ttu-id="b3b25-744">Den här funktionen stoppar mottagningen av gränssnittet för den allmänna seriella klassen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="b3b25-745">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b3b25-745">Parameters</span></span>

- <span data-ttu-id="b3b25-746">**gser** Pekare till gser-klass instansen.</span><span class="sxs-lookup"><span data-stu-id="b3b25-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="b3b25-747">**gser_reception** Struktur som innehåller mottagnings parametrarna</span><span class="sxs-lookup"><span data-stu-id="b3b25-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="b3b25-748">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b3b25-748">Return Value</span></span>

- <span data-ttu-id="b3b25-749">**UX_SUCCESS** (0x00) data överföringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="b3b25-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="b3b25-750">**UX_HOST_CLASS_UNKNOWN** (0X59) fel klass instans</span><span class="sxs-lookup"><span data-stu-id="b3b25-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="b3b25-751">**UX_ERROR** (0x01)-fel</span><span class="sxs-lookup"><span data-stu-id="b3b25-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="b3b25-752">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3b25-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
