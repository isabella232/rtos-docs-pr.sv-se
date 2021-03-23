---
title: Kapitel 4 – USBX PictBridge-implementering
description: UBSX stöder fullständig PictBridge-implementering både på värden och på enheten. PictBridge är ovanpå USBX PIMA-klassen på båda sidor.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2ef1809dac046d49b15aba000cabed6c9fd458a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828554"
---
# <a name="chapter-4---usbx-pictbridge-implementation"></a><span data-ttu-id="c1ac6-104">Kapitel 4 – USBX PictBridge-implementering</span><span class="sxs-lookup"><span data-stu-id="c1ac6-104">Chapter 4 - USBX Pictbridge implementation</span></span>

<span data-ttu-id="c1ac6-105">UBSX stöder fullständig PictBridge-implementering både på värden och på enheten.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="c1ac6-106">PictBridge är ovanpå USBX PIMA-klassen på båda sidor.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span>

<span data-ttu-id="c1ac6-107">PictBridge-standarden tillåter anslutning av en digital stillbilds kamera eller en smart telefon direkt till en skrivare utan en dator, vilket möjliggör direkt utskrift till vissa PictBridge-medvetna skrivare.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="c1ac6-108">När en kamera eller telefon är ansluten till en skrivare är skrivaren USB-värden och kameran är USB-enheten.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="c1ac6-109">Men med PictBridge visas kameran som värd och kommandona drivs från kameran.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="c1ac6-110">Kameran är lagrings servern, skrivaren på lagrings klienten.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="c1ac6-111">Kameran är utskrifts klienten och skrivaren är naturligtvis utskrifts servern.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-111">The camera is the print client and the printer is of course the print server.</span></span>

<span data-ttu-id="c1ac6-112">PictBridge använder USB som transport lager men förlitar sig på PTP (Picture Transfer Protocol) för kommunikations protokollet.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="c1ac6-113">Följande är ett diagram över kommandon/svar mellan DPS-klienten och DPS-servern när ett utskrifts jobb inträffar:</span><span class="sxs-lookup"><span data-stu-id="c1ac6-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs:</span></span>

![DPS-kommandon och-svar](./media/usbx-device-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="c1ac6-115">PictBridge-klient implementering</span><span class="sxs-lookup"><span data-stu-id="c1ac6-115">Pictbridge client implementation</span></span>

<span data-ttu-id="c1ac6-116">PictBridge på klienten kräver att USBX Device-stacken och PIMA-klassen körs först.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="c1ac6-117">Ett Device Framework beskriver PIMA-klassen på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-117">A device framework describes the PIMA class in the following way.</span></span>

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
    0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,
    /* Configuration descriptor */
    0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

<span data-ttu-id="c1ac6-118">Pima-klassen använder ID-fältet 0x06 och har underklassen är 0x01 för stillbild och protokollet är 0x01 för PIMA 15740.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="c1ac6-119">Tre slut punkter definieras i den här klassen. två mängder för att skicka/ta emot data och ett avbrott för händelser.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-119">Three endpoints are defined in this class; two bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="c1ac6-120">Till skillnad från andra USBX enhets implementeringar behöver inte PictBridge-programmet definiera en klass själva.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="c1ac6-121">I stället anropas funktionen ***ux_pictbridge_dpsclient_start***.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="c1ac6-122">Ett exempel är nedan.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-122">An example is below.</span></span>

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "ExpressLogic",13);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="c1ac6-123">De parametrar som skickas till PictBridge-klienten är följande.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-123">The parameters passed to the pictbridge client are as follows.</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no
    : String of serial number
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="c1ac6-124">Nästa steg är för enheten och värden för att synkronisera och vara redo att utbyta information.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="c1ac6-125">Detta görs genom att vänta på en händelse flagga på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-125">This is done by waiting on an event flag as follows.</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get(&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR,
    &actual_flags, UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="c1ac6-126">Om tillstånds datorn är i **DISCOVERY_COMPLETEs** tillstånd kommer kamera sidan (DPS-klienten) att samla in information om skrivaren och dess funktioner.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="c1ac6-127">Om DPS-klienten är redo att acceptera ett utskrifts jobb anges dess status till **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="c1ac6-128">Det kan kontrol leras nedan.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-128">It can be checked below.</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)
/* We can print something … */
```

<span data-ttu-id="c1ac6-129">Efterföljande joib-beskrivningar måste fyllas på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="c1ac6-129">Next some print joib descriptors need to be filled as follows:</span></span>

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo -> ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo -> ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo -> ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo -> ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */
printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object -> ux_device_class_pima_object_compressed_size = IMAGE_LEN;
object -> ux_device_class_pima_object_offset = 0;
object -> ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object -> ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

<span data-ttu-id="c1ac6-130">PictBridge-klienten har nu ett utskrifts jobb för att göra och hämtar avbildnings blocken i taget från programmet via det motanrop som definierats i fältet</span><span class="sxs-lookup"><span data-stu-id="c1ac6-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field</span></span>

```C
jobinfo -> ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="c1ac6-131">Prototypen för den funktionen definieras som:</span><span class="sxs-lookup"><span data-stu-id="c1ac6-131">The prototype of that function is defined as:</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="c1ac6-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="c1ac6-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="c1ac6-133">Kopiera ett data block från användar utrymmet för utskrift</span><span class="sxs-lookup"><span data-stu-id="c1ac6-133">Copying a block of data from user space for printing</span></span>

### <a name="prototype"></a><span data-ttu-id="c1ac6-134">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c1ac6-134">Prototype</span></span>

```C
UINT ux_pictbridge_jobinfo_object_data_read( 
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,  
    ULONG object_offset,  
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="c1ac6-135">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c1ac6-135">Description</span></span>

<span data-ttu-id="c1ac6-136">Den här funktionen anropas när DPS-klienten behöver hämta ett data block för att skriva ut till mål PictBridge-skrivaren.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="c1ac6-137">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c1ac6-137">Parameters</span></span>

- <span data-ttu-id="c1ac6-138">**PictBridge**: pekare till klass instansen PictBridge.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="c1ac6-139">**object_buffer**: pekar mot objekt-buffert</span><span class="sxs-lookup"><span data-stu-id="c1ac6-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="c1ac6-140">**object_offset**: där data blocket börjar läsas</span><span class="sxs-lookup"><span data-stu-id="c1ac6-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="c1ac6-141">**object_length**: längden som ska returneras</span><span class="sxs-lookup"><span data-stu-id="c1ac6-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="c1ac6-142">**actual_length**: den faktiska längden som returnerades</span><span class="sxs-lookup"><span data-stu-id="c1ac6-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="c1ac6-143">Returvärde</span><span class="sxs-lookup"><span data-stu-id="c1ac6-143">Return Value</span></span>

- <span data-ttu-id="c1ac6-144">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-144">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="c1ac6-145">**UX_ERROR** (0x01) programmet kunde inte hämta data.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-145">**UX_ERROR** (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="c1ac6-146">Exempel</span><span class="sxs-lookup"><span data-stu-id="c1ac6-146">Example</span></span>

```C
/* Copy the object data. */
UINT ux_demo_object_data_copy(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);
    /* Update the actual length. */
    *actual_length = object_length;
    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="c1ac6-147">PictBridge-värd implementering</span><span class="sxs-lookup"><span data-stu-id="c1ac6-147">Pictbridge host implementation</span></span>

<span data-ttu-id="c1ac6-148">Värd implementeringen av PictBridge skiljer sig från klienten.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="c1ac6-149">Det första du gör i en PictBridge-värd miljö är att registrera klassen Pima som exemplet nedan visar:</span><span class="sxs-lookup"><span data-stu-id="c1ac6-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(_ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="c1ac6-150">Den här klassen är det generiska PTP-lagret som sitter mellan USB-stacken och PictBridge-skiktet.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-150">This class is the generic PTP layer sitting between the USB stack and the Pictbridge layer.</span></span>

<span data-ttu-id="c1ac6-151">Nästa steg är att initiera PictBridge-standardvärden för utskrifts tjänster enligt följande:</span><span class="sxs-lookup"><span data-stu-id="c1ac6-151">The next step is to initialize the Pictbridge default values for print services as follows:</span></span>

| <span data-ttu-id="c1ac6-152">PictBridge-fält</span><span class="sxs-lookup"><span data-stu-id="c1ac6-152">Pictbridge field</span></span>       | <span data-ttu-id="c1ac6-153">Värde</span><span class="sxs-lookup"><span data-stu-id="c1ac6-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="c1ac6-154">DpsVersion [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-154">DpsVersion[0]</span></span>          | <span data-ttu-id="c1ac6-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="c1ac6-155">0x00010000</span></span>                             |
| <span data-ttu-id="c1ac6-156">DpsVersion [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-156">DpsVersion[1]</span></span>          | <span data-ttu-id="c1ac6-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="c1ac6-157">0x00010001</span></span>                             |
| <span data-ttu-id="c1ac6-158">DpsVersion [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-158">DpsVersion[2]</span></span>          | <span data-ttu-id="c1ac6-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="c1ac6-159">0x00000000</span></span>                             |
| <span data-ttu-id="c1ac6-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="c1ac6-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="c1ac6-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="c1ac6-161">0x00010000</span></span>                             |
| <span data-ttu-id="c1ac6-162">PrintServiceAvailable</span><span class="sxs-lookup"><span data-stu-id="c1ac6-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="c1ac6-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="c1ac6-163">0x30010000</span></span>                             |
| <span data-ttu-id="c1ac6-164">Kvaliteter [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-164">Qualities[0]</span></span>           | <span data-ttu-id="c1ac6-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="c1ac6-166">Kvaliteter [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-166">Qualities[1]</span></span>           | <span data-ttu-id="c1ac6-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="c1ac6-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="c1ac6-168">Kvaliteter [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-168">Qualities[2]</span></span>           | <span data-ttu-id="c1ac6-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="c1ac6-170">Kvaliteter [3]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-170">Qualities[3]</span></span>           | <span data-ttu-id="c1ac6-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="c1ac6-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="c1ac6-172">PaperSizes [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-172">PaperSizes[0]</span></span>          | <span data-ttu-id="c1ac6-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="c1ac6-174">PaperSizes [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-174">PaperSizes[1]</span></span>          | <span data-ttu-id="c1ac6-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="c1ac6-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="c1ac6-176">PaperSizes [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-176">PaperSizes[2]</span></span>          | <span data-ttu-id="c1ac6-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="c1ac6-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="c1ac6-178">PaperSizes [3]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-178">PaperSizes[3]</span></span>          | <span data-ttu-id="c1ac6-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="c1ac6-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="c1ac6-180">PaperSizes [4]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-180">PaperSizes[4]</span></span>          | <span data-ttu-id="c1ac6-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="c1ac6-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="c1ac6-182">PaperTypes [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-182">PaperTypes[0]</span></span>          | <span data-ttu-id="c1ac6-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="c1ac6-184">PaperTypes [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-184">PaperTypes[1]</span></span>          | <span data-ttu-id="c1ac6-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="c1ac6-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="c1ac6-186">PaperTypes [2</span><span class="sxs-lookup"><span data-stu-id="c1ac6-186">PaperTypes[2</span></span>           | <span data-ttu-id="c1ac6-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="c1ac6-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="c1ac6-188">Filtypen [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-188">FileTypes[0]</span></span>           | <span data-ttu-id="c1ac6-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="c1ac6-190">Filtypen [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-190">FileTypes[1]</span></span>           | <span data-ttu-id="c1ac6-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="c1ac6-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="c1ac6-192">Filtypen [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-192">FileTypes[2]</span></span>           | <span data-ttu-id="c1ac6-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="c1ac6-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="c1ac6-194">Filfiltyp [3]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-194">FileTypes[3]</span></span>           | <span data-ttu-id="c1ac6-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="c1ac6-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="c1ac6-196">DatePrints [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-196">DatePrints[0]</span></span>          | <span data-ttu-id="c1ac6-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="c1ac6-198">DatePrints [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-198">DatePrints[1]</span></span>          | <span data-ttu-id="c1ac6-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="c1ac6-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="c1ac6-200">DatePrints [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-200">DatePrints[2]</span></span>          | <span data-ttu-id="c1ac6-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="c1ac6-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="c1ac6-202">FileNamePrints [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="c1ac6-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="c1ac6-204">FileNamePrints [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="c1ac6-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="c1ac6-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="c1ac6-206">FileNamePrints [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="c1ac6-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="c1ac6-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="c1ac6-208">ImageOptimizes [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="c1ac6-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="c1ac6-210">ImageOptimizes [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="c1ac6-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="c1ac6-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="c1ac6-212">ImageOptimizes [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="c1ac6-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="c1ac6-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="c1ac6-214">Layouter [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-214">Layouts[0]</span></span>             | <span data-ttu-id="c1ac6-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="c1ac6-216">Layouter [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-216">Layouts[1]</span></span>             | <span data-ttu-id="c1ac6-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="c1ac6-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="c1ac6-218">Layouter [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-218">Layouts[2]</span></span>             | <span data-ttu-id="c1ac6-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="c1ac6-220">Layouter [3]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-220">Layouts[3]</span></span>             | <span data-ttu-id="c1ac6-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="c1ac6-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="c1ac6-222">FixedSizes [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-222">FixedSizes[0]</span></span>          | <span data-ttu-id="c1ac6-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="c1ac6-224">FixedSizes [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-224">FixedSizes[1]</span></span>          | <span data-ttu-id="c1ac6-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="c1ac6-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="c1ac6-226">FixedSizes [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-226">FixedSizes[2]</span></span>          | <span data-ttu-id="c1ac6-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="c1ac6-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="c1ac6-228">FixedSizes [3]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-228">FixedSizes[3]</span></span>          | <span data-ttu-id="c1ac6-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="c1ac6-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="c1ac6-230">FixedSizes [4]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-230">FixedSizes[4]</span></span>          | <span data-ttu-id="c1ac6-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="c1ac6-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="c1ac6-232">FixedSizes [5]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-232">FixedSizes[5]</span></span>          | <span data-ttu-id="c1ac6-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="c1ac6-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="c1ac6-234">FixedSizes [6]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-234">FixedSizes[6]</span></span>          | <span data-ttu-id="c1ac6-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="c1ac6-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="c1ac6-236">Beskärningar [0]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-236">Croppings[0]</span></span>           | <span data-ttu-id="c1ac6-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c1ac6-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="c1ac6-238">Beskärningar [1]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-238">Croppings[1]</span></span>           | <span data-ttu-id="c1ac6-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="c1ac6-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="c1ac6-240">Beskärningar [2]</span><span class="sxs-lookup"><span data-stu-id="c1ac6-240">Croppings[2]</span></span>           | <span data-ttu-id="c1ac6-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="c1ac6-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="c1ac6-242">Tillstånds datorn för DPS-värden ställs in på inaktiv och är redo att acceptera ett nytt utskrifts jobb.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="c1ac6-243">Värd delen av PictBridge kan nu startas som exemplet nedan visar:</span><span class="sxs-lookup"><span data-stu-id="c1ac6-243">The host portion of Pictbridge can now be started as the example below shows:</span></span>

```C
/* Activate the pictbridge dpshost. */
status = ux_pictbridge_dpshost_start(&pictbridge, pima);

if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="c1ac6-244">Funktionen PictBridge Host kräver ett motanrop när data är klara att skrivas ut.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="c1ac6-245">Detta åstadkommer du genom att skicka en funktions pekare i den PictBridge värd strukturen enligt följande.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */
pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="c1ac6-246">Den här funktionen har följande egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-246">This function has the following properties.</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="c1ac6-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="c1ac6-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="c1ac6-248">Skriva ett data block för utskrift</span><span class="sxs-lookup"><span data-stu-id="c1ac6-248">Writing a block of data for printing</span></span>

### <a name="prototype"></a><span data-ttu-id="c1ac6-249">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c1ac6-249">Prototype</span></span>

```C
UINT ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge, 
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="c1ac6-250">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c1ac6-250">Description</span></span>

<span data-ttu-id="c1ac6-251">Den här funktionen anropas när DPS-servern behöver hämta ett data block från DPS-klienten för att skriva ut till den lokala skrivaren.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="c1ac6-252">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c1ac6-252">Parameters</span></span>

- <span data-ttu-id="c1ac6-253">**PictBridge**: pekare till klass instansen PictBridge.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="c1ac6-254">**object_buffer**: pekar mot objekt-buffert</span><span class="sxs-lookup"><span data-stu-id="c1ac6-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="c1ac6-255">**object_offset**: där data blocket börjar läsas</span><span class="sxs-lookup"><span data-stu-id="c1ac6-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="c1ac6-256">**total_length**: hela objekt längden</span><span class="sxs-lookup"><span data-stu-id="c1ac6-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="c1ac6-257">**längd**: buffertens längd</span><span class="sxs-lookup"><span data-stu-id="c1ac6-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="c1ac6-258">Returvärde</span><span class="sxs-lookup"><span data-stu-id="c1ac6-258">Return Value</span></span>

- <span data-ttu-id="c1ac6-259">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-259">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="c1ac6-260">**UX_ERROR** (0x01) programmet kunde inte skriva ut data.</span><span class="sxs-lookup"><span data-stu-id="c1ac6-260">**UX_ERROR** (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="c1ac6-261">Exempel</span><span class="sxs-lookup"><span data-stu-id="c1ac6-261">Example</span></span>

```C
/* Copy the object data. */
UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;
    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
