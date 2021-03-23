---
title: Kapitel 5 – överväganden för enhets klass i USBX
description: Lär dig mer om USBX enhets klass överväganden.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826541"
---
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="913a2-103">Kapitel 5 – överväganden för enhets klass i USBX</span><span class="sxs-lookup"><span data-stu-id="913a2-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="913a2-104">Registrering av enhets klass</span><span class="sxs-lookup"><span data-stu-id="913a2-104">Device Class registration</span></span>

<span data-ttu-id="913a2-105">Varje enhets klass följer samma princip för registrering.</span><span class="sxs-lookup"><span data-stu-id="913a2-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="913a2-106">En struktur som innehåller vissa klass parametrar skickas till klass initierings funktionen.</span><span class="sxs-lookup"><span data-stu-id="913a2-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

<span data-ttu-id="913a2-107">Varje klass kan registreras, om du vill, en callback-funktion när en instans av klassen aktive ras.</span><span class="sxs-lookup"><span data-stu-id="913a2-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="913a2-108">Återanropet anropas sedan av enhets stacken för att informera programmet om att en instans har skapats.</span><span class="sxs-lookup"><span data-stu-id="913a2-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="913a2-109">Programmet skulle ha i sitt innehåll 2 funktioner för aktivering och inaktive ring, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="913a2-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

<span data-ttu-id="913a2-110">Vi rekommenderar inte att du gör något i dessa funktioner, men för att komma ihåg instansen av klassen och synkronisera med resten av programmet.</span><span class="sxs-lookup"><span data-stu-id="913a2-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="913a2-111">Lagrings klass för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="913a2-111">USB Device Storage Class</span></span>

<span data-ttu-id="913a2-112">Lagrings klassen USB-enhet gör det möjligt för en lagrings enhet som är inbäddad i systemet att göras synlig för en USB-värd.</span><span class="sxs-lookup"><span data-stu-id="913a2-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="913a2-113">USB-enhetens lagrings klass tillhandahåller inte någon lagrings lösning.</span><span class="sxs-lookup"><span data-stu-id="913a2-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="913a2-114">Den accepterar bara och tolkar de SCSI-begäranden som kommer från värden.</span><span class="sxs-lookup"><span data-stu-id="913a2-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="913a2-115">När en av dessa begär Anden är ett Läs-eller Skriv kommando, anropar den ett fördefinierat anrop till en riktig lagrings enhets hanterare, till exempel en ATA-drivrutin eller en driv rutin för Flash-enheter.</span><span class="sxs-lookup"><span data-stu-id="913a2-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="913a2-116">När enhetens lagrings klass initieras, tilldelas en pekare till den klass som innehåller all information som behövs.</span><span class="sxs-lookup"><span data-stu-id="913a2-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="913a2-117">Ett exempel anges nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-117">An example is given below.</span></span>

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

<span data-ttu-id="913a2-118">I det här exemplet är driv Rutinens lagrings strängar anpassade genom att tilldela sträng pekare till motsvarande parameter.</span><span class="sxs-lookup"><span data-stu-id="913a2-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="913a2-119">Om någon av sträng pekarna lämnas till UX_NULL används standard strängen för Azure-återställnings tider.</span><span class="sxs-lookup"><span data-stu-id="913a2-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="913a2-120">I det här exemplet anges enhetens senaste block adress eller LBA och storleken på den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="913a2-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="913a2-121">LBA är antalet sektorer som är tillgängliga i mediet – 1.</span><span class="sxs-lookup"><span data-stu-id="913a2-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="913a2-122">Block längden anges till 512 i det vanliga lagrings mediet.</span><span class="sxs-lookup"><span data-stu-id="913a2-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="913a2-123">Den kan ställas in på 2048 för optiska enheter.</span><span class="sxs-lookup"><span data-stu-id="913a2-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="913a2-124">Programmet måste klara tre återanrops funktions pekare för att tillåta lagrings klassen att läsa, skriva och hämta status för mediet.</span><span class="sxs-lookup"><span data-stu-id="913a2-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="913a2-125">Prototyperna för Läs-och skriv funktionerna visas i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-125">The prototypes for the read and write functions are shown in the example below.</span></span>

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

<span data-ttu-id="913a2-126">Plats:</span><span class="sxs-lookup"><span data-stu-id="913a2-126">Where:</span></span>

- <span data-ttu-id="913a2-127">*Storage* är instansen av lagrings klassen.</span><span class="sxs-lookup"><span data-stu-id="913a2-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="913a2-128">*LUN* är den LUN som kommandot dirigeras till.</span><span class="sxs-lookup"><span data-stu-id="913a2-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="913a2-129">*data_pointer* är adressen till den buffert som ska användas för att läsa eller skriva.</span><span class="sxs-lookup"><span data-stu-id="913a2-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="913a2-130">*number_blocks* är antalet sektorer som ska läsas/skrivas.</span><span class="sxs-lookup"><span data-stu-id="913a2-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="913a2-131">*LBA* är sektor adressen som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="913a2-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="913a2-132">*media_status* ska fyllas i exakt som retur värde för medie status.</span><span class="sxs-lookup"><span data-stu-id="913a2-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="913a2-133">Returvärdet kan antingen ha värdet UX_SUCCESS eller UX_ERROR som anger att åtgärden lyckades eller misslyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="913a2-134">Dessa åtgärder behöver inte returnera andra felkoder.</span><span class="sxs-lookup"><span data-stu-id="913a2-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="913a2-135">Om det uppstår ett fel i en åtgärd, kommer lagrings klassen att anropa funktionen för status anrops återställning.</span><span class="sxs-lookup"><span data-stu-id="913a2-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="913a2-136">Den här funktionen har följande prototyp.</span><span class="sxs-lookup"><span data-stu-id="913a2-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="913a2-137">Den anropande parametern media_id används inte för närvarande och bör alltid vara 0.</span><span class="sxs-lookup"><span data-stu-id="913a2-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="913a2-138">I framtiden kan det användas för att särskilja flera lagrings enheter eller lagrings enheter med flera SCSI-LUN.</span><span class="sxs-lookup"><span data-stu-id="913a2-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="913a2-139">Den här versionen av lagrings klassen har inte stöd för flera instanser av lagrings klassen eller lagrings enheter med flera SCSI-LUN.</span><span class="sxs-lookup"><span data-stu-id="913a2-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="913a2-140">Returvärdet är en SCSI-felkod som kan ha följande format.</span><span class="sxs-lookup"><span data-stu-id="913a2-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="913a2-141">**Bits 0-7** Sense_key</span><span class="sxs-lookup"><span data-stu-id="913a2-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="913a2-142">**Bits 8-15** Ytterligare Sense-kod</span><span class="sxs-lookup"><span data-stu-id="913a2-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="913a2-143">**Bits 16-23** Ytterligare Sense Code-kvalificerare</span><span class="sxs-lookup"><span data-stu-id="913a2-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="913a2-144">I följande tabell finns möjliga kombinationer för Sense/ASC/ASCQ.</span><span class="sxs-lookup"><span data-stu-id="913a2-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="913a2-145">Sense-nyckel</span><span class="sxs-lookup"><span data-stu-id="913a2-145">Sense Key</span></span> | <span data-ttu-id="913a2-146">ASC</span><span class="sxs-lookup"><span data-stu-id="913a2-146">ASC</span></span> | <span data-ttu-id="913a2-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="913a2-147">ASCQ</span></span> | <span data-ttu-id="913a2-148">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="913a2-149">00</span><span class="sxs-lookup"><span data-stu-id="913a2-149">00</span></span>        | <span data-ttu-id="913a2-150">00</span><span class="sxs-lookup"><span data-stu-id="913a2-150">00</span></span>  | <span data-ttu-id="913a2-151">00</span><span class="sxs-lookup"><span data-stu-id="913a2-151">00</span></span>   | <span data-ttu-id="913a2-152">INGEN KÄNSLA</span><span class="sxs-lookup"><span data-stu-id="913a2-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="913a2-153">01</span><span class="sxs-lookup"><span data-stu-id="913a2-153">01</span></span>        | <span data-ttu-id="913a2-154">17</span><span class="sxs-lookup"><span data-stu-id="913a2-154">17</span></span>  | <span data-ttu-id="913a2-155">01</span><span class="sxs-lookup"><span data-stu-id="913a2-155">01</span></span>   | <span data-ttu-id="913a2-156">ÅTERSTÄLLDA DATA MED ÅTERFÖRSÖK</span><span class="sxs-lookup"><span data-stu-id="913a2-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="913a2-157">01</span><span class="sxs-lookup"><span data-stu-id="913a2-157">01</span></span>        | <span data-ttu-id="913a2-158">18</span><span class="sxs-lookup"><span data-stu-id="913a2-158">18</span></span>  | <span data-ttu-id="913a2-159">00</span><span class="sxs-lookup"><span data-stu-id="913a2-159">00</span></span>   | <span data-ttu-id="913a2-160">ÅTERSTÄLLDA DATA MED ECC</span><span class="sxs-lookup"><span data-stu-id="913a2-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="913a2-161">02</span><span class="sxs-lookup"><span data-stu-id="913a2-161">02</span></span>        | <span data-ttu-id="913a2-162">04</span><span class="sxs-lookup"><span data-stu-id="913a2-162">04</span></span>  | <span data-ttu-id="913a2-163">01</span><span class="sxs-lookup"><span data-stu-id="913a2-163">01</span></span>   | <span data-ttu-id="913a2-164">DEN LOGISKA ENHETEN ÄR INTE KLAR – BLI KLAR</span><span class="sxs-lookup"><span data-stu-id="913a2-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="913a2-165">02</span><span class="sxs-lookup"><span data-stu-id="913a2-165">02</span></span>        | <span data-ttu-id="913a2-166">04</span><span class="sxs-lookup"><span data-stu-id="913a2-166">04</span></span>  | <span data-ttu-id="913a2-167">02</span><span class="sxs-lookup"><span data-stu-id="913a2-167">02</span></span>   | <span data-ttu-id="913a2-168">DEN LOGISKA ENHETEN ÄR INTE KLAR-INITIERING KRÄVS</span><span class="sxs-lookup"><span data-stu-id="913a2-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="913a2-169">02</span><span class="sxs-lookup"><span data-stu-id="913a2-169">02</span></span>        | <span data-ttu-id="913a2-170">04</span><span class="sxs-lookup"><span data-stu-id="913a2-170">04</span></span>  | <span data-ttu-id="913a2-171">04</span><span class="sxs-lookup"><span data-stu-id="913a2-171">04</span></span>   | <span data-ttu-id="913a2-172">DEN LOGISKA ENHETEN ÄR INTE KLAR-FORMAT PÅGÅR</span><span class="sxs-lookup"><span data-stu-id="913a2-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="913a2-173">02</span><span class="sxs-lookup"><span data-stu-id="913a2-173">02</span></span>        | <span data-ttu-id="913a2-174">04</span><span class="sxs-lookup"><span data-stu-id="913a2-174">04</span></span>  | <span data-ttu-id="913a2-175">FF</span><span class="sxs-lookup"><span data-stu-id="913a2-175">FF</span></span>   | <span data-ttu-id="913a2-176">DEN LOGISKA ENHETEN ÄR INTE KLAR-ENHETEN ÄR UPPTAGEN</span><span class="sxs-lookup"><span data-stu-id="913a2-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="913a2-177">02</span><span class="sxs-lookup"><span data-stu-id="913a2-177">02</span></span>        | <span data-ttu-id="913a2-178">06</span><span class="sxs-lookup"><span data-stu-id="913a2-178">06</span></span>  | <span data-ttu-id="913a2-179">00</span><span class="sxs-lookup"><span data-stu-id="913a2-179">00</span></span>   | <span data-ttu-id="913a2-180">INGEN REFERENS POSITION HITTADES</span><span class="sxs-lookup"><span data-stu-id="913a2-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="913a2-181">02</span><span class="sxs-lookup"><span data-stu-id="913a2-181">02</span></span>        | <span data-ttu-id="913a2-182">08</span><span class="sxs-lookup"><span data-stu-id="913a2-182">08</span></span>  | <span data-ttu-id="913a2-183">00</span><span class="sxs-lookup"><span data-stu-id="913a2-183">00</span></span>   | <span data-ttu-id="913a2-184">KOMMUNIKATIONS PROBLEM MED LOGISK ENHET</span><span class="sxs-lookup"><span data-stu-id="913a2-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="913a2-185">02</span><span class="sxs-lookup"><span data-stu-id="913a2-185">02</span></span>        | <span data-ttu-id="913a2-186">08</span><span class="sxs-lookup"><span data-stu-id="913a2-186">08</span></span>  | <span data-ttu-id="913a2-187">01</span><span class="sxs-lookup"><span data-stu-id="913a2-187">01</span></span>   | <span data-ttu-id="913a2-188">TIMEOUT FÖR KOMMUNIKATION AV LOGISK ENHET</span><span class="sxs-lookup"><span data-stu-id="913a2-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="913a2-189">02</span><span class="sxs-lookup"><span data-stu-id="913a2-189">02</span></span>        | <span data-ttu-id="913a2-190">08</span><span class="sxs-lookup"><span data-stu-id="913a2-190">08</span></span>  | <span data-ttu-id="913a2-191">80</span><span class="sxs-lookup"><span data-stu-id="913a2-191">80</span></span>   | <span data-ttu-id="913a2-192">BUFFERTÖVERSKRIDNING VID KOMMUNIKATION MELLAN LOGISKA ENHETER</span><span class="sxs-lookup"><span data-stu-id="913a2-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="913a2-193">02</span><span class="sxs-lookup"><span data-stu-id="913a2-193">02</span></span>        | <span data-ttu-id="913a2-194">Punkterna</span><span class="sxs-lookup"><span data-stu-id="913a2-194">3A</span></span>  | <span data-ttu-id="913a2-195">00</span><span class="sxs-lookup"><span data-stu-id="913a2-195">00</span></span>   | <span data-ttu-id="913a2-196">MEDIUM SAKNAS</span><span class="sxs-lookup"><span data-stu-id="913a2-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="913a2-197">02</span><span class="sxs-lookup"><span data-stu-id="913a2-197">02</span></span>        | <span data-ttu-id="913a2-198">54</span><span class="sxs-lookup"><span data-stu-id="913a2-198">54</span></span>  | <span data-ttu-id="913a2-199">00</span><span class="sxs-lookup"><span data-stu-id="913a2-199">00</span></span>   | <span data-ttu-id="913a2-200">USB TILL VÄRD FÖR SYSTEM GRÄNSSNITTS PROBLEM</span><span class="sxs-lookup"><span data-stu-id="913a2-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="913a2-201">02</span><span class="sxs-lookup"><span data-stu-id="913a2-201">02</span></span>        | <span data-ttu-id="913a2-202">80</span><span class="sxs-lookup"><span data-stu-id="913a2-202">80</span></span>  | <span data-ttu-id="913a2-203">00</span><span class="sxs-lookup"><span data-stu-id="913a2-203">00</span></span>   | <span data-ttu-id="913a2-204">OTILLRÄCKLIGA RESURSER</span><span class="sxs-lookup"><span data-stu-id="913a2-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="913a2-205">02</span><span class="sxs-lookup"><span data-stu-id="913a2-205">02</span></span>        | <span data-ttu-id="913a2-206">FF</span><span class="sxs-lookup"><span data-stu-id="913a2-206">FF</span></span>  | <span data-ttu-id="913a2-207">FF</span><span class="sxs-lookup"><span data-stu-id="913a2-207">FF</span></span>   | <span data-ttu-id="913a2-208">OKÄNT FEL</span><span class="sxs-lookup"><span data-stu-id="913a2-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="913a2-209">03</span><span class="sxs-lookup"><span data-stu-id="913a2-209">03</span></span>        | <span data-ttu-id="913a2-210">02</span><span class="sxs-lookup"><span data-stu-id="913a2-210">02</span></span>  | <span data-ttu-id="913a2-211">00</span><span class="sxs-lookup"><span data-stu-id="913a2-211">00</span></span>   | <span data-ttu-id="913a2-212">INGEN SÖKNING HAR SLUTFÖRTS</span><span class="sxs-lookup"><span data-stu-id="913a2-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="913a2-213">03</span><span class="sxs-lookup"><span data-stu-id="913a2-213">03</span></span>        | <span data-ttu-id="913a2-214">03</span><span class="sxs-lookup"><span data-stu-id="913a2-214">03</span></span>  | <span data-ttu-id="913a2-215">00</span><span class="sxs-lookup"><span data-stu-id="913a2-215">00</span></span>   | <span data-ttu-id="913a2-216">SKRIV FEL</span><span class="sxs-lookup"><span data-stu-id="913a2-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="913a2-217">03</span><span class="sxs-lookup"><span data-stu-id="913a2-217">03</span></span>        | <span data-ttu-id="913a2-218">10</span><span class="sxs-lookup"><span data-stu-id="913a2-218">10</span></span>  | <span data-ttu-id="913a2-219">00</span><span class="sxs-lookup"><span data-stu-id="913a2-219">00</span></span>   | <span data-ttu-id="913a2-220">ID-CRC-FEL</span><span class="sxs-lookup"><span data-stu-id="913a2-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="913a2-221">03</span><span class="sxs-lookup"><span data-stu-id="913a2-221">03</span></span>        | <span data-ttu-id="913a2-222">11</span><span class="sxs-lookup"><span data-stu-id="913a2-222">11</span></span>  | <span data-ttu-id="913a2-223">00</span><span class="sxs-lookup"><span data-stu-id="913a2-223">00</span></span>   | <span data-ttu-id="913a2-224">LÄSFEL SOM INTE HAR ÅTERSTÄLLTS</span><span class="sxs-lookup"><span data-stu-id="913a2-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="913a2-225">03</span><span class="sxs-lookup"><span data-stu-id="913a2-225">03</span></span>        | <span data-ttu-id="913a2-226">12</span><span class="sxs-lookup"><span data-stu-id="913a2-226">12</span></span>  | <span data-ttu-id="913a2-227">00</span><span class="sxs-lookup"><span data-stu-id="913a2-227">00</span></span>   | <span data-ttu-id="913a2-228">ADRESS MARKERINGEN HITTADES INTE FÖR FÄLTET ID</span><span class="sxs-lookup"><span data-stu-id="913a2-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="913a2-229">03</span><span class="sxs-lookup"><span data-stu-id="913a2-229">03</span></span>        | <span data-ttu-id="913a2-230">13</span><span class="sxs-lookup"><span data-stu-id="913a2-230">13</span></span>  | <span data-ttu-id="913a2-231">00</span><span class="sxs-lookup"><span data-stu-id="913a2-231">00</span></span>   | <span data-ttu-id="913a2-232">DET GICK INTE ATT HITTA ADRESS MARKERINGEN FÖR DATA FÄLTET</span><span class="sxs-lookup"><span data-stu-id="913a2-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="913a2-233">03</span><span class="sxs-lookup"><span data-stu-id="913a2-233">03</span></span>        | <span data-ttu-id="913a2-234">14</span><span class="sxs-lookup"><span data-stu-id="913a2-234">14</span></span>  | <span data-ttu-id="913a2-235">00</span><span class="sxs-lookup"><span data-stu-id="913a2-235">00</span></span>   | <span data-ttu-id="913a2-236">DEN REGISTRERADE ENTITETEN HITTADES INTE</span><span class="sxs-lookup"><span data-stu-id="913a2-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="913a2-237">03</span><span class="sxs-lookup"><span data-stu-id="913a2-237">03</span></span>        | <span data-ttu-id="913a2-238">30</span><span class="sxs-lookup"><span data-stu-id="913a2-238">30</span></span>  | <span data-ttu-id="913a2-239">01</span><span class="sxs-lookup"><span data-stu-id="913a2-239">01</span></span>   | <span data-ttu-id="913a2-240">DET GÅR INTE ATT LÄSA MEDIUM-OKÄNT FORMAT</span><span class="sxs-lookup"><span data-stu-id="913a2-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="913a2-241">03</span><span class="sxs-lookup"><span data-stu-id="913a2-241">03</span></span>        | <span data-ttu-id="913a2-242">31</span><span class="sxs-lookup"><span data-stu-id="913a2-242">31</span></span>  | <span data-ttu-id="913a2-243">01</span><span class="sxs-lookup"><span data-stu-id="913a2-243">01</span></span>   | <span data-ttu-id="913a2-244">FORMAT KOMMANDOT MISSLYCKADES</span><span class="sxs-lookup"><span data-stu-id="913a2-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="913a2-245">04</span><span class="sxs-lookup"><span data-stu-id="913a2-245">04</span></span>        | <span data-ttu-id="913a2-246">40</span><span class="sxs-lookup"><span data-stu-id="913a2-246">40</span></span>  | <span data-ttu-id="913a2-247">NN</span><span class="sxs-lookup"><span data-stu-id="913a2-247">NN</span></span>   | <span data-ttu-id="913a2-248">DIAGNOSTISKT FEL PÅ KOMPONENTEN NN (80H-FFH)</span><span class="sxs-lookup"><span data-stu-id="913a2-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="913a2-249">05</span><span class="sxs-lookup"><span data-stu-id="913a2-249">05</span></span>        | <span data-ttu-id="913a2-250">6.1</span><span class="sxs-lookup"><span data-stu-id="913a2-250">1A</span></span>  | <span data-ttu-id="913a2-251">00</span><span class="sxs-lookup"><span data-stu-id="913a2-251">00</span></span>   | <span data-ttu-id="913a2-252">PARAMETER LIST LÄNGD FEL</span><span class="sxs-lookup"><span data-stu-id="913a2-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="913a2-253">05</span><span class="sxs-lookup"><span data-stu-id="913a2-253">05</span></span>        | <span data-ttu-id="913a2-254">20</span><span class="sxs-lookup"><span data-stu-id="913a2-254">20</span></span>  | <span data-ttu-id="913a2-255">00</span><span class="sxs-lookup"><span data-stu-id="913a2-255">00</span></span>   | <span data-ttu-id="913a2-256">OGILTIG KOMMANDO ÅTGÄRDS KOD</span><span class="sxs-lookup"><span data-stu-id="913a2-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="913a2-257">05</span><span class="sxs-lookup"><span data-stu-id="913a2-257">05</span></span>        | <span data-ttu-id="913a2-258">21</span><span class="sxs-lookup"><span data-stu-id="913a2-258">21</span></span>  | <span data-ttu-id="913a2-259">00</span><span class="sxs-lookup"><span data-stu-id="913a2-259">00</span></span>   | <span data-ttu-id="913a2-260">LOGISK BLOCK ADRESS UTANFÖR INTERVALLET</span><span class="sxs-lookup"><span data-stu-id="913a2-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="913a2-261">05</span><span class="sxs-lookup"><span data-stu-id="913a2-261">05</span></span>        | <span data-ttu-id="913a2-262">24</span><span class="sxs-lookup"><span data-stu-id="913a2-262">24</span></span>  | <span data-ttu-id="913a2-263">00</span><span class="sxs-lookup"><span data-stu-id="913a2-263">00</span></span>   | <span data-ttu-id="913a2-264">OGILTIGT FÄLT I KOMMANDO PAKET</span><span class="sxs-lookup"><span data-stu-id="913a2-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="913a2-265">05</span><span class="sxs-lookup"><span data-stu-id="913a2-265">05</span></span>        | <span data-ttu-id="913a2-266">25</span><span class="sxs-lookup"><span data-stu-id="913a2-266">25</span></span>  | <span data-ttu-id="913a2-267">00</span><span class="sxs-lookup"><span data-stu-id="913a2-267">00</span></span>   | <span data-ttu-id="913a2-268">LOGISK ENHET STÖDS INTE</span><span class="sxs-lookup"><span data-stu-id="913a2-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="913a2-269">05</span><span class="sxs-lookup"><span data-stu-id="913a2-269">05</span></span>        | <span data-ttu-id="913a2-270">26</span><span class="sxs-lookup"><span data-stu-id="913a2-270">26</span></span>  | <span data-ttu-id="913a2-271">00</span><span class="sxs-lookup"><span data-stu-id="913a2-271">00</span></span>   | <span data-ttu-id="913a2-272">OGILTIGT FÄLT I PARAMETER LISTAN</span><span class="sxs-lookup"><span data-stu-id="913a2-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="913a2-273">05</span><span class="sxs-lookup"><span data-stu-id="913a2-273">05</span></span>        | <span data-ttu-id="913a2-274">26</span><span class="sxs-lookup"><span data-stu-id="913a2-274">26</span></span>  | <span data-ttu-id="913a2-275">01</span><span class="sxs-lookup"><span data-stu-id="913a2-275">01</span></span>   | <span data-ttu-id="913a2-276">PARAMETERN STÖDS INTE</span><span class="sxs-lookup"><span data-stu-id="913a2-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="913a2-277">05</span><span class="sxs-lookup"><span data-stu-id="913a2-277">05</span></span>        | <span data-ttu-id="913a2-278">26</span><span class="sxs-lookup"><span data-stu-id="913a2-278">26</span></span>  | <span data-ttu-id="913a2-279">02</span><span class="sxs-lookup"><span data-stu-id="913a2-279">02</span></span>   | <span data-ttu-id="913a2-280">OGILTIGT PARAMETER VÄRDE</span><span class="sxs-lookup"><span data-stu-id="913a2-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="913a2-281">05</span><span class="sxs-lookup"><span data-stu-id="913a2-281">05</span></span>        | <span data-ttu-id="913a2-282">39</span><span class="sxs-lookup"><span data-stu-id="913a2-282">39</span></span>  | <span data-ttu-id="913a2-283">00</span><span class="sxs-lookup"><span data-stu-id="913a2-283">00</span></span>   | <span data-ttu-id="913a2-284">ATT SPARA PARAMETRAR STÖDS INTE</span><span class="sxs-lookup"><span data-stu-id="913a2-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="913a2-285">06</span><span class="sxs-lookup"><span data-stu-id="913a2-285">06</span></span>        | <span data-ttu-id="913a2-286">28</span><span class="sxs-lookup"><span data-stu-id="913a2-286">28</span></span>  | <span data-ttu-id="913a2-287">00</span><span class="sxs-lookup"><span data-stu-id="913a2-287">00</span></span>   | <span data-ttu-id="913a2-288">ÄR INTE REDO FÖR REDO ÖVER GÅNG – MEDIET HAR ÄNDRATS</span><span class="sxs-lookup"><span data-stu-id="913a2-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="913a2-289">06</span><span class="sxs-lookup"><span data-stu-id="913a2-289">06</span></span>        | <span data-ttu-id="913a2-290">29</span><span class="sxs-lookup"><span data-stu-id="913a2-290">29</span></span>  | <span data-ttu-id="913a2-291">00</span><span class="sxs-lookup"><span data-stu-id="913a2-291">00</span></span>   | <span data-ttu-id="913a2-292">ÅTERSTÄLLNING AV STRÖM VID ÅTERSTÄLLNING ELLER BUSS ENHETS ÅTERSTÄLLNING UTFÖRDES</span><span class="sxs-lookup"><span data-stu-id="913a2-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="913a2-293">06</span><span class="sxs-lookup"><span data-stu-id="913a2-293">06</span></span>        | <span data-ttu-id="913a2-294">2F</span><span class="sxs-lookup"><span data-stu-id="913a2-294">2F</span></span>  | <span data-ttu-id="913a2-295">00</span><span class="sxs-lookup"><span data-stu-id="913a2-295">00</span></span>   | <span data-ttu-id="913a2-296">KOMMANDON SOM RENSATS AV EN ANNAN INITIERARE</span><span class="sxs-lookup"><span data-stu-id="913a2-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="913a2-297">07</span><span class="sxs-lookup"><span data-stu-id="913a2-297">07</span></span>        | <span data-ttu-id="913a2-298">27</span><span class="sxs-lookup"><span data-stu-id="913a2-298">27</span></span>  | <span data-ttu-id="913a2-299">00</span><span class="sxs-lookup"><span data-stu-id="913a2-299">00</span></span>   | <span data-ttu-id="913a2-300">SKRIV SKYDDADE MEDIA</span><span class="sxs-lookup"><span data-stu-id="913a2-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="913a2-301">0B</span><span class="sxs-lookup"><span data-stu-id="913a2-301">0B</span></span>        | <span data-ttu-id="913a2-302">4E</span><span class="sxs-lookup"><span data-stu-id="913a2-302">4E</span></span>  | <span data-ttu-id="913a2-303">00</span><span class="sxs-lookup"><span data-stu-id="913a2-303">00</span></span>   | <span data-ttu-id="913a2-304">ÖVERLAPPANDE KOMMANDO FÖRSÖK</span><span class="sxs-lookup"><span data-stu-id="913a2-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="913a2-305">Det finns två ytterligare, valfria återanrop som programmet kan implementera. ett för att svara på ett **GET_STATUS_NOTIFICATION** kommando och det andra är att svara på **SYNCHRONIZE_CACHE** kommandot.</span><span class="sxs-lookup"><span data-stu-id="913a2-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="913a2-306">Om programmet vill hantera GET_STATUS_NOTIFICATION kommandot från värden ska det implementera ett återanrop med följande prototyp.</span><span class="sxs-lookup"><span data-stu-id="913a2-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="913a2-307">Plats:</span><span class="sxs-lookup"><span data-stu-id="913a2-307">Where:</span></span>

- <span data-ttu-id="913a2-308">*Storage* är instansen av lagrings klassen.</span><span class="sxs-lookup"><span data-stu-id="913a2-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="913a2-309">*media_id* används inte för närvarande.</span><span class="sxs-lookup"><span data-stu-id="913a2-309">*media_id* is not currently used.</span></span> <span data-ttu-id="913a2-310">notification_class anger klassen för meddelandet.</span><span class="sxs-lookup"><span data-stu-id="913a2-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="913a2-311">*media_notification* ska anges av programmet till den buffert som innehåller svaret på aviseringen.</span><span class="sxs-lookup"><span data-stu-id="913a2-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="913a2-312">*media_notification_length* ska anges av programmet som ska innehålla längden på svars bufferten.</span><span class="sxs-lookup"><span data-stu-id="913a2-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="913a2-313">Returvärdet anger om kommandot lyckades eller inte ska vara antingen **UX_SUCCESS** eller **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="913a2-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="913a2-314">Om programmet inte implementerar det här återanropet, kommer USBX att meddela värden att kommandot inte har implementerats när du tar emot kommandot **GET_STATUS_NOTIFICATION** .</span><span class="sxs-lookup"><span data-stu-id="913a2-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="913a2-315">Kommandot **SYNCHRONIZE_CACHE** bör hanteras om programmet använder ett cacheminne för skrivningar från värden.</span><span class="sxs-lookup"><span data-stu-id="913a2-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="913a2-316">En värd kan skicka det här kommandot om det vet att lagrings enheten ska kopplas från, till exempel i Windows, om du högerklickar på en enhets ikon i verktygsfältet och väljer "Mata ut \[ lagrings enhets namn \] ", kommer Windows att utfärda **SYNCHRONIZE_CACHE** kommandot till den enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="913a2-317">Om programmet vill hantera **GET_STATUS_NOTIFICATION** kommandot från värden ska det implementera ett återanrop med följande prototyp.</span><span class="sxs-lookup"><span data-stu-id="913a2-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="913a2-318">Plats:</span><span class="sxs-lookup"><span data-stu-id="913a2-318">Where:</span></span>

- <span data-ttu-id="913a2-319">*Storage* är instansen av lagrings klassen.</span><span class="sxs-lookup"><span data-stu-id="913a2-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="913a2-320">*LUN* -parameter anger vilken LUN som kommandot dirigeras till.</span><span class="sxs-lookup"><span data-stu-id="913a2-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="913a2-321">*number_blocks* anger antalet block som ska synkroniseras.</span><span class="sxs-lookup"><span data-stu-id="913a2-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="913a2-322">*LBA* är sektor adressen för det första blocket som ska synkroniseras.</span><span class="sxs-lookup"><span data-stu-id="913a2-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="913a2-323">*media_status* ska fyllas i exakt som retur värde för medie status.</span><span class="sxs-lookup"><span data-stu-id="913a2-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="913a2-324">Returvärdet anger om kommandot lyckades eller inte ska vara antingen **UX_SUCCESS** eller **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="913a2-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="913a2-325">Flera SCSI-LUN</span><span class="sxs-lookup"><span data-stu-id="913a2-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="913a2-326">Enhetens lagrings klass för USBX stöder flera LUN.</span><span class="sxs-lookup"><span data-stu-id="913a2-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="913a2-327">Därför är det möjligt att skapa en lagrings enhet som fungerar som en CD-ROM-skiva och en flash-disk på samma tid.</span><span class="sxs-lookup"><span data-stu-id="913a2-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="913a2-328">I sådana fall skulle initieringen skilja sig något.</span><span class="sxs-lookup"><span data-stu-id="913a2-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="913a2-329">Här är ett exempel på en flash-disk och CD-ROM:</span><span class="sxs-lookup"><span data-stu-id="913a2-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="913a2-330">USB-enhet CDC-ACM-klass</span><span class="sxs-lookup"><span data-stu-id="913a2-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="913a2-331">USB-enhetens CDC-ACM-klass gör att ett USB-värdnamn kan kommunicera med enheten som en seriell enhet.</span><span class="sxs-lookup"><span data-stu-id="913a2-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="913a2-332">Den här klassen baseras på USB-standarden och är en delmängd av CDC-standarden.</span><span class="sxs-lookup"><span data-stu-id="913a2-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="913a2-333">Ett CDC-ACM-kompatibelt enhets ramverk måste deklareras av enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="913a2-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="913a2-334">Ett exempel finns här nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-334">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

<span data-ttu-id="913a2-335">Klassen CDC-ACM använder en sammansatt enhets ramverk för att gruppera gränssnitt (kontroll och data).</span><span class="sxs-lookup"><span data-stu-id="913a2-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="913a2-336">Därför bör du vidta åtgärder när du definierar enhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="913a2-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="913a2-337">USBX förlitar sig på IAD-beskrivningen för att veta internt hur man binder gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="913a2-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="913a2-338">IAD-beskrivningen måste deklareras före gränssnitten och innehålla det första gränssnittet i CDC-ACM-klassen och hur många gränssnitt som är kopplade till dem.</span><span class="sxs-lookup"><span data-stu-id="913a2-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="913a2-339">Klassen CDC-ACM använder också en funktions beskrivning för union som utför samma funktion som den nyare IAD-beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="913a2-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="913a2-340">Även om en union funktions beskrivning måste deklareras för historiska orsaker och kompatibilitet med värd sidan, används den inte av USBX.</span><span class="sxs-lookup"><span data-stu-id="913a2-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="913a2-341">Initieringen av CDC-ACM-klassen förväntar sig följande parametrar.</span><span class="sxs-lookup"><span data-stu-id="913a2-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="913a2-342">De två definierade parametrarna är callback-pekare i de användar program som anropas när stacken aktive ras eller inaktive ras i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="913a2-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="913a2-343">Den tredje parametern som definierats är en callback-pekare till det användar program som kommer att anropas när det finns en parameter ändring i rad kod eller rad status.</span><span class="sxs-lookup"><span data-stu-id="913a2-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="913a2-344">T. ex., om det finns en begäran från värden för att ändra DTR-tillståndet till **True**, anropas återanropet i det användar program som kan kontrol lera rad tillstånd genom IOCTL-funktionen för att Kow-värden är klar för kommunikation.</span><span class="sxs-lookup"><span data-stu-id="913a2-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="913a2-345">CDC-ACM baseras på en USB-IF-standard och identifieras automatiskt av MACOs och Linux-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="913a2-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="913a2-346">På Windows-plattformar kräver den här klassen en INF-fil för Windows-version före 10.</span><span class="sxs-lookup"><span data-stu-id="913a2-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="913a2-347">Windows 10 kräver inte några INF-filer.</span><span class="sxs-lookup"><span data-stu-id="913a2-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="913a2-348">Vi tillhandahåller en mall för CDC-ACM-klassen, som du hittar i ***usbx_windows_host_files*** -katalogen.</span><span class="sxs-lookup"><span data-stu-id="913a2-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="913a2-349">För senare versioner av Windows ska filen CDC_ACM_Template_Win7_64bit. inf användas (förutom Win10).</span><span class="sxs-lookup"><span data-stu-id="913a2-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="913a2-350">Den här filen måste ändras för att återspegla det PID/VID som används av enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="913a2-351">PID/VID är specifika för den slutgiltiga kunden när företaget och produkten registreras med USB-IF.</span><span class="sxs-lookup"><span data-stu-id="913a2-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="913a2-352">I INF-filen finns fälten som ska ändras här.</span><span class="sxs-lookup"><span data-stu-id="913a2-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="913a2-353">I enhets ramverket för CDC-ACM-enheten lagras PID/VID i enhets beskrivningen (se den enhets beskrivning som anges ovan).</span><span class="sxs-lookup"><span data-stu-id="913a2-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="913a2-354">När ett USB-värdnamn identifierar USB CDC-ACM-enheten kommer den att montera en serie klass och enheten kan användas med alla seriella terminaler-program.</span><span class="sxs-lookup"><span data-stu-id="913a2-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="913a2-355">Se värd operativ systemet för referens.</span><span class="sxs-lookup"><span data-stu-id="913a2-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="913a2-356">API-funktionerna för CDC-ACM-klass definieras nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="913a2-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="913a2-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="913a2-358">Utföra IOCTL på CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-359">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-360">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-360">Description</span></span>

<span data-ttu-id="913a2-361">Den här funktionen anropas när ett program behöver utföra olika IOCTL-anrop till CDC ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-362">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-362">Parameters</span></span>

- <span data-ttu-id="913a2-363">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-364">**ioctl_function**: IOCTL-funktion som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="913a2-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="913a2-365">**parameter**: pekar mot en parameter som är speciell för IOCTL-anropet.</span><span class="sxs-lookup"><span data-stu-id="913a2-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="913a2-366">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-366">Return Value</span></span>

- <span data-ttu-id="913a2-367">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-368">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="913a2-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="913a2-369">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="913a2-370">IOCTL-funktioner:</span><span class="sxs-lookup"><span data-stu-id="913a2-370">Ioctl functions:</span></span>

| <span data-ttu-id="913a2-371">Funktion</span><span class="sxs-lookup"><span data-stu-id="913a2-371">Function</span></span>                                        | <span data-ttu-id="913a2-372">Värde</span><span class="sxs-lookup"><span data-stu-id="913a2-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="913a2-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="913a2-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="913a2-374">1</span><span class="sxs-lookup"><span data-stu-id="913a2-374">1</span></span> |
| <span data-ttu-id="913a2-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="913a2-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="913a2-376">2</span><span class="sxs-lookup"><span data-stu-id="913a2-376">2</span></span> |
| <span data-ttu-id="913a2-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="913a2-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="913a2-378">3</span><span class="sxs-lookup"><span data-stu-id="913a2-378">3</span></span> |
| <span data-ttu-id="913a2-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="913a2-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="913a2-380">4</span><span class="sxs-lookup"><span data-stu-id="913a2-380">4</span></span> |
| <span data-ttu-id="913a2-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="913a2-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="913a2-382">5</span><span class="sxs-lookup"><span data-stu-id="913a2-382">5</span></span> |
| <span data-ttu-id="913a2-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="913a2-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="913a2-384">6</span><span class="sxs-lookup"><span data-stu-id="913a2-384">6</span></span> |
| <span data-ttu-id="913a2-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="913a2-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="913a2-386">7</span><span class="sxs-lookup"><span data-stu-id="913a2-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="913a2-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="913a2-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="913a2-388">Utför IOCTL-uppsättningens rad kodning i CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-389">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-390">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-390">Description</span></span>

<span data-ttu-id="913a2-391">Den här funktionen anropas när ett program behöver ange rad kodnings parametrar.</span><span class="sxs-lookup"><span data-stu-id="913a2-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-392">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-392">Parameters</span></span>

- <span data-ttu-id="913a2-393">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="913a2-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="913a2-395">**parameter**: pekare till en linje parameter struktur:</span><span class="sxs-lookup"><span data-stu-id="913a2-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="913a2-396">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-396">Return Value</span></span>

<span data-ttu-id="913a2-397">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-398">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-398">Example</span></span>

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="913a2-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="913a2-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="913a2-400">Utför IOCTL-kodning på CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-401">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-402">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-402">Description</span></span>

<span data-ttu-id="913a2-403">Den här funktionen anropas när ett program behöver hämta rad kodnings parametrarna.</span><span class="sxs-lookup"><span data-stu-id="913a2-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-404">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-404">Parameters</span></span>

- <span data-ttu-id="913a2-405">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="913a2-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="913a2-407">**parameter**: pekare till en linje parameter struktur:</span><span class="sxs-lookup"><span data-stu-id="913a2-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="913a2-408">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-408">Return Value</span></span>

- <span data-ttu-id="913a2-409">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-410">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-410">Example</span></span>

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="913a2-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="913a2-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="913a2-412">Utför IOCTL Hämta linje tillstånd på CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="913a2-413">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-414">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-414">Description</span></span>

<span data-ttu-id="913a2-415">Den här funktionen anropas när ett program behöver hämta linje tillstånds parametrarna.</span><span class="sxs-lookup"><span data-stu-id="913a2-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-416">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-416">Parameters</span></span>

- <span data-ttu-id="913a2-417">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="913a2-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="913a2-419">**parameter**: pekare till en linje parameter struktur:</span><span class="sxs-lookup"><span data-stu-id="913a2-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="913a2-420">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-420">Return Value</span></span>

- <span data-ttu-id="913a2-421">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-422">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-422">Example</span></span>

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="913a2-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="913a2-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="913a2-424">Ange linje tillstånd för IOCTL-uppsättning på CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-425">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-426">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-426">Description</span></span>

<span data-ttu-id="913a2-427">Den här funktionen anropas när ett program behöver hämta parametrar för linje tillstånd</span><span class="sxs-lookup"><span data-stu-id="913a2-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-428">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-428">Parameters</span></span>

- <span data-ttu-id="913a2-429">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="913a2-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="913a2-431">**parameter**: pekare till en linje parameter struktur:</span><span class="sxs-lookup"><span data-stu-id="913a2-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="913a2-432">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-432">Return Value</span></span>

- <span data-ttu-id="913a2-433">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-434">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="913a2-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="913a2-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="913a2-436">Utföra IOCTL ABORT-PIPE på CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-437">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-438">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-438">Description</span></span>

<span data-ttu-id="913a2-439">Den här funktionen anropas när ett program måste avbryta en pipe.</span><span class="sxs-lookup"><span data-stu-id="913a2-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="913a2-440">Om du till exempel vill avbryta en pågående skrivning ska UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT skickas som parametern.</span><span class="sxs-lookup"><span data-stu-id="913a2-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-441">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-441">Parameters</span></span>

- <span data-ttu-id="913a2-442">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="913a2-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="913a2-444">**parameter**: riktningen för rör:</span><span class="sxs-lookup"><span data-stu-id="913a2-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="913a2-445">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-445">Return Value</span></span>

- <span data-ttu-id="913a2-446">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0X53) ogiltig rör riktning.</span><span class="sxs-lookup"><span data-stu-id="913a2-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-448">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="913a2-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="913a2-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="913a2-450">Starta IOCTL-överföring på gränssnittet CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="913a2-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-451">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-452">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-452">Description</span></span>

<span data-ttu-id="913a2-453">Den här funktionen anropas när ett program vill använda överföring med motringning.</span><span class="sxs-lookup"><span data-stu-id="913a2-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-454">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-454">Parameters</span></span>

- <span data-ttu-id="913a2-455">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="913a2-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="913a2-457">**parameter**: pekare till den Start överförings parameter strukturen:</span><span class="sxs-lookup"><span data-stu-id="913a2-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="913a2-458">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-458">Return Value</span></span>

- <span data-ttu-id="913a2-459">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-460">**UX_ERROR** (0xFF)-överföringen har redan startats.</span><span class="sxs-lookup"><span data-stu-id="913a2-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="913a2-461">**UX_MEMORY_INSUFFICIENT** (0X12) en minnesallokering misslyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-462">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-462">Example</span></span>

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="913a2-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="913a2-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="913a2-464">Stoppa IOCTL-överföringen på CDC-ACM-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="913a2-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="913a2-466">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-466">Description</span></span>

<span data-ttu-id="913a2-467">Den här funktionen anropas när ett program vill sluta använda överföring med motringning.</span><span class="sxs-lookup"><span data-stu-id="913a2-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-468">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-468">Parameters</span></span>

- <span data-ttu-id="913a2-469">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span><span class="sxs-lookup"><span data-stu-id="913a2-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="913a2-471">**parameter**: används inte</span><span class="sxs-lookup"><span data-stu-id="913a2-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="913a2-472">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-472">Return Value</span></span>

- <span data-ttu-id="913a2-473">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-474">**UX_ERROR** (0Xff) ingen kontinuerlig överföring.</span><span class="sxs-lookup"><span data-stu-id="913a2-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-475">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="913a2-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="913a2-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="913a2-477">Läsa från CDC-ACM-pipe</span><span class="sxs-lookup"><span data-stu-id="913a2-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-478">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="913a2-479">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-479">Description</span></span>

<span data-ttu-id="913a2-480">Den här funktionen anropas när ett program behöver läsa från indata-pipen (ut från värden i från enheten).</span><span class="sxs-lookup"><span data-stu-id="913a2-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="913a2-481">Den blockeras.</span><span class="sxs-lookup"><span data-stu-id="913a2-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-482">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-482">Parameters</span></span>

- <span data-ttu-id="913a2-483">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-484">**Buffer**: buffertens adress där data ska lagras.</span><span class="sxs-lookup"><span data-stu-id="913a2-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="913a2-485">**requested_length**: den maximala längden som vi förväntar dig.</span><span class="sxs-lookup"><span data-stu-id="913a2-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="913a2-486">**actual_length**: längden som returnerades i bufferten.</span><span class="sxs-lookup"><span data-stu-id="913a2-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="913a2-487">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-487">Return Value</span></span>

- <span data-ttu-id="913a2-488">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** -enheten (0x51) är inte längre i det konfigurerade läget.</span><span class="sxs-lookup"><span data-stu-id="913a2-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="913a2-490">**UX_TRANSFER_NO_ANSWER** (0X22) inget svar från enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="913a2-491">Enheten var förmodligen frånkopplad medan överföringen väntade.</span><span class="sxs-lookup"><span data-stu-id="913a2-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-492">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="913a2-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="913a2-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="913a2-494">Skriva till en CDC-ACM-pipe</span><span class="sxs-lookup"><span data-stu-id="913a2-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-495">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="913a2-496">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-496">Description</span></span>

<span data-ttu-id="913a2-497">Den här funktionen anropas när ett program behöver skriva till i data-pipe (från värden från-enheten).</span><span class="sxs-lookup"><span data-stu-id="913a2-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="913a2-498">Den blockeras.</span><span class="sxs-lookup"><span data-stu-id="913a2-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-499">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-499">Parameters</span></span>

- <span data-ttu-id="913a2-500">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-501">**Buffer**: buffertens adress där data lagras.</span><span class="sxs-lookup"><span data-stu-id="913a2-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="913a2-502">**requested_length**: längden på bufferten som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="913a2-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="913a2-503">**actual_length**: längden som returnerades till bufferten efter skrivning utförs.</span><span class="sxs-lookup"><span data-stu-id="913a2-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="913a2-504">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-504">Return Value</span></span>
- <span data-ttu-id="913a2-505">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** -enheten (0x51) är inte längre i det konfigurerade läget.</span><span class="sxs-lookup"><span data-stu-id="913a2-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="913a2-507">**UX_TRANSFER_NO_ANSWER** (0X22) inget svar från enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="913a2-508">Enheten var förmodligen frånkopplad medan överföringen väntade.</span><span class="sxs-lookup"><span data-stu-id="913a2-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-509">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="913a2-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="913a2-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="913a2-511">Skriver till en CDC-ACM-pipe med motringning</span><span class="sxs-lookup"><span data-stu-id="913a2-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-512">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="913a2-513">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-513">Description</span></span>

<span data-ttu-id="913a2-514">Den här funktionen anropas när ett program behöver skriva till i data-pipe (från värden från-enheten).</span><span class="sxs-lookup"><span data-stu-id="913a2-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="913a2-515">Den här funktionen är inte blockerad och slut för ande görs via en motringning som anges i UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span><span class="sxs-lookup"><span data-stu-id="913a2-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-516">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-516">Parameters</span></span>

- <span data-ttu-id="913a2-517">**cdc_acm**: pekar mot CDC-klassens instans.</span><span class="sxs-lookup"><span data-stu-id="913a2-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="913a2-518">**Buffer**: buffertens adress där data lagras.</span><span class="sxs-lookup"><span data-stu-id="913a2-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="913a2-519">**requested_length**: längden på bufferten som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="913a2-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="913a2-520">**actual_length**: längden som returnerades till bufferten efter skrivning utförs</span><span class="sxs-lookup"><span data-stu-id="913a2-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="913a2-521">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-521">Return Value</span></span>

- <span data-ttu-id="913a2-522">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** -enheten (0x51) är inte längre i det konfigurerade läget.</span><span class="sxs-lookup"><span data-stu-id="913a2-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="913a2-524">**UX_TRANSFER_NO_ANSWER** (0X22) inget svar från enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="913a2-525">Enheten var förmodligen frånkopplad medan överföringen väntade.</span><span class="sxs-lookup"><span data-stu-id="913a2-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-526">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="913a2-527">USB-enhet CDC-ECM-klass</span><span class="sxs-lookup"><span data-stu-id="913a2-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="913a2-528">USB-enhet CDC-ECM-klassen gör att ett USB-värdnamn kan kommunicera med enheten som en Ethernet-enhet.</span><span class="sxs-lookup"><span data-stu-id="913a2-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="913a2-529">Den här klassen baseras på USB-standarden och är en delmängd av CDC-standarden.</span><span class="sxs-lookup"><span data-stu-id="913a2-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="913a2-530">Ett CDC-ACM-kompatibelt enhets ramverk måste deklareras av enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="913a2-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="913a2-531">Ett exempel finns här nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-531">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

<span data-ttu-id="913a2-532">CDC-ECM-klassen använder en mycket liknande enhets beskrivnings metod för CDC-ACM och kräver även en IAD-beskrivning.</span><span class="sxs-lookup"><span data-stu-id="913a2-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="913a2-533">Se CDC-ACM-klassen för definition.</span><span class="sxs-lookup"><span data-stu-id="913a2-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="913a2-534">Förutom det vanliga enhets ramverket kräver CDC-ECM särskilda sträng beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="913a2-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="913a2-535">Ett exempel anges nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-535">An example is given below.</span></span>

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

<span data-ttu-id="913a2-536">Beskrivningen av MAC-adress strängen används av CDC-ECM-klassen för att svara på värd frågor som den MAC-adress som enheten svarar på på TCP/IP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="913a2-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="913a2-537">Den kan ställas in på enhets valet men måste definieras här.</span><span class="sxs-lookup"><span data-stu-id="913a2-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="913a2-538">Initieringen av CDC-ECM-klassen är följande.</span><span class="sxs-lookup"><span data-stu-id="913a2-538">The initialization of the CDC-ECM class is as follows.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

<span data-ttu-id="913a2-539">Initieringen av den här klassen förväntar sig samma funktions återanrop för aktivering och inaktive ring, även om den är inställd på NULL så att ingen motringning utförs.</span><span class="sxs-lookup"><span data-stu-id="913a2-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="913a2-540">Nästa parametrar är för definitionen av nod-ID: n.</span><span class="sxs-lookup"><span data-stu-id="913a2-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="913a2-541">2 noder krävs för CDC-ECM, en lokal nod och en fjärrnod.</span><span class="sxs-lookup"><span data-stu-id="913a2-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="913a2-542">Den lokala noden anger enhetens MAC-adress, medan fjärrnoden anger värdens MAC-adress.</span><span class="sxs-lookup"><span data-stu-id="913a2-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="913a2-543">Fjärrnoden måste vara samma som den som har deklarerats i enhets ramverkets sträng beskrivning.</span><span class="sxs-lookup"><span data-stu-id="913a2-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="913a2-544">CDC-ECM-klassen har inbyggda API: er för överföring av data på båda sätt, men de är dolda för programmet när användar programmet kommer att kommunicera med USB Ethernet-enheten via NetX.</span><span class="sxs-lookup"><span data-stu-id="913a2-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="913a2-545">USBX CDC-ECM-klassen är nära kopplad till Azure återställnings tider NetX Network stack.</span><span class="sxs-lookup"><span data-stu-id="913a2-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="913a2-546">Ett program som använder både NetX och USBX CDC-ECM-klass kommer att aktivera NetX-nätverks stacken på vanligt sätt, men du måste också aktivera USB-protokollstacken på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="913a2-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="913a2-547">USB-protokollstacken behöver bara aktive ras en gång och är inte särskilt för CDCECM, men krävs av alla USB-klasser som kräver NetX-tjänster.</span><span class="sxs-lookup"><span data-stu-id="913a2-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="913a2-548">CDC-ECM-klassen kommer att identifieras av MAC OS-och Linux-värdar.</span><span class="sxs-lookup"><span data-stu-id="913a2-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="913a2-549">Men det finns ingen driv rutin som tillhandahålls av Microsoft Windows för att identifiera CDC-ECM internt.</span><span class="sxs-lookup"><span data-stu-id="913a2-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="913a2-550">Vissa kommersiella produkter finns för Windows-plattformar och de tillhandahåller sin egen. inf-fil.</span><span class="sxs-lookup"><span data-stu-id="913a2-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="913a2-551">Den här filen måste ändras på samma sätt som inf-mallen för CDC-ACM för att matcha PID/VID-USB-enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="913a2-552">HID-klass för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="913a2-552">USB Device HID Class</span></span>

<span data-ttu-id="913a2-553">Med HID-klassen USB-enhet kan ett USB-värdnamn ansluta till en HID-enhet med vissa funktioner för HID-klienter.</span><span class="sxs-lookup"><span data-stu-id="913a2-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="913a2-554">USBX HID-enhets klass är relativt enkel jämfört med värd sidan.</span><span class="sxs-lookup"><span data-stu-id="913a2-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="913a2-555">Den är nära knuten till enhetens funktions sätt och dess HID-beskrivning.</span><span class="sxs-lookup"><span data-stu-id="913a2-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="913a2-556">Alla HID-klienter måste först definiera ett HID Device Framework som i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="913a2-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

<span data-ttu-id="913a2-557">HID-ramverket innehåller en gränssnitts beskrivning som beskriver klassen HID och underklassen HID-enhet.</span><span class="sxs-lookup"><span data-stu-id="913a2-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="913a2-558">HID-gränssnittet kan vara en fristående klass eller en del av en sammansatt enhet.</span><span class="sxs-lookup"><span data-stu-id="913a2-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="913a2-559">För närvarande stöder USBX HID-klassen inte flera rapport-ID: n eftersom de flesta program bara kräver ett ID (ID noll).</span><span class="sxs-lookup"><span data-stu-id="913a2-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="913a2-560">Kontakta oss om flera rapport-ID: n är en funktion som du är intresse rad av.</span><span class="sxs-lookup"><span data-stu-id="913a2-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="913a2-561">Initieringen av HID-klassen är som följer med ett USB-tangentbord som exempel.</span><span class="sxs-lookup"><span data-stu-id="913a2-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

<span data-ttu-id="913a2-562">Programmet måste skicka till HID-klassen en rapport beskrivning med en HID-rapport och dess längd.</span><span class="sxs-lookup"><span data-stu-id="913a2-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="913a2-563">Rapport beskrivningen är en samling objekt som beskriver enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="913a2-564">Mer information om HID-grammatiken hittar du i specifikationen HID USB-klass.</span><span class="sxs-lookup"><span data-stu-id="913a2-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="913a2-565">Förutom rapport beskrivningen skickar programmet ett anrop tillbaka när en HID-händelse inträffar.</span><span class="sxs-lookup"><span data-stu-id="913a2-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="913a2-566">USBX HID-klassen stöder följande HID-standardkommandon från värden.</span><span class="sxs-lookup"><span data-stu-id="913a2-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="913a2-567">Kommando namn</span><span class="sxs-lookup"><span data-stu-id="913a2-567">Command name</span></span>                             | <span data-ttu-id="913a2-568">Värde</span><span class="sxs-lookup"><span data-stu-id="913a2-568">Value</span></span> | <span data-ttu-id="913a2-569">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="913a2-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="913a2-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="913a2-571">0x01</span><span class="sxs-lookup"><span data-stu-id="913a2-571">0x01</span></span>  | <span data-ttu-id="913a2-572">Hämta en rapport från enheten</span><span class="sxs-lookup"><span data-stu-id="913a2-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="913a2-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="913a2-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="913a2-574">0x02</span><span class="sxs-lookup"><span data-stu-id="913a2-574">0x02</span></span>  | <span data-ttu-id="913a2-575">Hämta vilo läges frekvensen för avbrotts slut punkten</span><span class="sxs-lookup"><span data-stu-id="913a2-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="913a2-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="913a2-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="913a2-577">0x03</span><span class="sxs-lookup"><span data-stu-id="913a2-577">0x03</span></span>  | <span data-ttu-id="913a2-578">Hämta protokollet som körs på enheten</span><span class="sxs-lookup"><span data-stu-id="913a2-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="913a2-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="913a2-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="913a2-580">0x09</span><span class="sxs-lookup"><span data-stu-id="913a2-580">0x09</span></span>  | <span data-ttu-id="913a2-581">Ställ in en rapport på enheten</span><span class="sxs-lookup"><span data-stu-id="913a2-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="913a2-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="913a2-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="913a2-583">0x0A</span><span class="sxs-lookup"><span data-stu-id="913a2-583">0x0a</span></span>  | <span data-ttu-id="913a2-584">Ange inaktivitet för avbrotts slut punkten</span><span class="sxs-lookup"><span data-stu-id="913a2-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="913a2-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="913a2-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="913a2-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="913a2-586">0x0b</span></span>  | <span data-ttu-id="913a2-587">Hämta protokollet som körs på enheten</span><span class="sxs-lookup"><span data-stu-id="913a2-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="913a2-588">Rapporten hämta och ange är de vanligaste kommandona av HID för att överföra data fram och tillbaka mellan värden och enheten.</span><span class="sxs-lookup"><span data-stu-id="913a2-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="913a2-589">Oftast skickar värden data på kontroll slut punkten, men kan ta emot data antingen på avbrotts slut punkten eller genom att utfärda ett GET_REPORT-kommando för att hämta data på kontroll slut punkten.</span><span class="sxs-lookup"><span data-stu-id="913a2-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="913a2-590">Klassen HID kan skicka data tillbaka till värden på avbrotts slut punkten med hjälp av funktionen ux_device_class_hid_event_set.</span><span class="sxs-lookup"><span data-stu-id="913a2-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="913a2-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="913a2-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="913a2-592">Ställa in en händelse på HID-klassen</span><span class="sxs-lookup"><span data-stu-id="913a2-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-593">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="913a2-594">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-594">Description</span></span>

<span data-ttu-id="913a2-595">Den här funktionen anropas när ett program behöver skicka en HID-händelse tillbaka till värden.</span><span class="sxs-lookup"><span data-stu-id="913a2-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="913a2-596">Funktionen blockeras inte, den placerar bara rapporten i en cirkulär kö och återgår till programmet.</span><span class="sxs-lookup"><span data-stu-id="913a2-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-597">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-597">Parameters</span></span>

- <span data-ttu-id="913a2-598">**HID**: pekar mot klass instansen HID.</span><span class="sxs-lookup"><span data-stu-id="913a2-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="913a2-599">**hid_event**: pekaren till strukturen för HID-händelsen.</span><span class="sxs-lookup"><span data-stu-id="913a2-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="913a2-600">Returvärde</span><span class="sxs-lookup"><span data-stu-id="913a2-600">Return Value</span></span>

- <span data-ttu-id="913a2-601">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="913a2-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="913a2-602">**UX_ERROR** (0Xff) fel ledigt utrymme i cirkulär kö.</span><span class="sxs-lookup"><span data-stu-id="913a2-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-603">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-603">Example</span></span>

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

<span data-ttu-id="913a2-604">Återanropet som definieras vid initieringen av HID-klassen utför motsatsen till att skicka en händelse.</span><span class="sxs-lookup"><span data-stu-id="913a2-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="913a2-605">Den tar emot den händelse som skickas av värden.</span><span class="sxs-lookup"><span data-stu-id="913a2-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="913a2-606">Prototypen för återanropet är följande.</span><span class="sxs-lookup"><span data-stu-id="913a2-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="913a2-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="913a2-607">hid_callback</span></span>

<span data-ttu-id="913a2-608">Hämta en händelse från HID-klassen</span><span class="sxs-lookup"><span data-stu-id="913a2-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="913a2-609">Prototyp</span><span class="sxs-lookup"><span data-stu-id="913a2-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="913a2-610">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="913a2-610">Description</span></span>

<span data-ttu-id="913a2-611">Den här funktionen anropas när värden skickar en HID-rapport till programmet.</span><span class="sxs-lookup"><span data-stu-id="913a2-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="913a2-612">Parametrar</span><span class="sxs-lookup"><span data-stu-id="913a2-612">Parameters</span></span>

- <span data-ttu-id="913a2-613">**HID**: pekar mot klass instansen HID.</span><span class="sxs-lookup"><span data-stu-id="913a2-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="913a2-614">**hid_event**: pekaren till strukturen för HID-händelsen.</span><span class="sxs-lookup"><span data-stu-id="913a2-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="913a2-615">Exempel</span><span class="sxs-lookup"><span data-stu-id="913a2-615">Example</span></span>

<span data-ttu-id="913a2-616">I följande exempel visas hur du tolkar en händelse för ett HID-tangentbord:</span><span class="sxs-lookup"><span data-stu-id="913a2-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
