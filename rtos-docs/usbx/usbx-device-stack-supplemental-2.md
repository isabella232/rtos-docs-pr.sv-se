---
title: Kapitel 2 – överväganden för enhets klass i USBX
description: USB-enhetens RNDIS-klass tillåter att ett USB-värdnamn kommunicerar med enheten som en Ethernet-enhet. Den här klassen baseras på Microsofts patentskyddade implementering och är specifika för Windows-plattformar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082225"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="b7310-104">Kapitel 2 – överväganden för enhets klass i USBX</span><span class="sxs-lookup"><span data-stu-id="b7310-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="b7310-105">RNDIS-klass för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="b7310-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="b7310-106">USB-enhetens RNDIS-klass tillåter att ett USB-värdnamn kommunicerar med enheten som en Ethernet-enhet.</span><span class="sxs-lookup"><span data-stu-id="b7310-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="b7310-107">Den här klassen baseras på Microsofts patentskyddade implementering och är specifika för Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="b7310-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="b7310-108">Ett RNDIS-kompatibelt enhets ramverk måste deklareras av enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="b7310-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="b7310-109">Ett exempel finns nedan.</span><span class="sxs-lookup"><span data-stu-id="b7310-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="b7310-110">RNDIS-klassen använder en mycket liknande enhets beskrivnings metod för CDC-ACM och CDC-ECM och kräver också en IAD-beskrivning.</span><span class="sxs-lookup"><span data-stu-id="b7310-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="b7310-111">Se CDC-ACM-klassen för definition och krav för enhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="b7310-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="b7310-112">Aktiveringen av RNDIS-klassen är följande.</span><span class="sxs-lookup"><span data-stu-id="b7310-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="b7310-113">För CDC-ECM kräver RNDIS-klassen 2 noder, en lokal och en fjärr anslutning, men det finns inget krav på att ha en sträng beskrivning som beskriver fjärrnoden.</span><span class="sxs-lookup"><span data-stu-id="b7310-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="b7310-114">Men på grund av Microsoft patentskyddad meddelande funktion krävs vissa extra parametrar.</span><span class="sxs-lookup"><span data-stu-id="b7310-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="b7310-115">Först måste leverantörs-ID: t skickas.</span><span class="sxs-lookup"><span data-stu-id="b7310-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="b7310-116">På samma sätt är driv rutins versionen av RNDIS.</span><span class="sxs-lookup"><span data-stu-id="b7310-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="b7310-117">En leverantörs sträng måste också anges.</span><span class="sxs-lookup"><span data-stu-id="b7310-117">A vendor string must also be given.</span></span>

<span data-ttu-id="b7310-118">RNDIS-klassen har inbyggda API: er för överföring av data på båda sätt, men de är dolda för programmet när användar programmet kommer att kommunicera med USB-Ethernet-enheten via NetX.</span><span class="sxs-lookup"><span data-stu-id="b7310-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="b7310-119">USBX RNDIS-klassen är nära kopplad till Azure återställnings tider NetX-nätverks stacken.</span><span class="sxs-lookup"><span data-stu-id="b7310-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="b7310-120">Ett program som använder både NetX-och USBX RNDIS-klassen kommer att aktivera NetX-nätverks stacken på vanligt sätt, men du måste också aktivera USB-protokollstacken på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="b7310-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="b7310-121">USB-protokollstacken behöver bara aktive ras en gång och är inte särskilt för RNDIS, men krävs av alla USB-klasser som kräver NetX-tjänster.</span><span class="sxs-lookup"><span data-stu-id="b7310-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="b7310-122">RNDIS-klassen känns inte igen av MAC OS-och Linux-värdar eftersom den är speciell för Microsofts operativ system.</span><span class="sxs-lookup"><span data-stu-id="b7310-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="b7310-123">På Windows-plattformar måste en INF-fil finnas på den värd som matchar enhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="b7310-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="b7310-124">Microsoft tillhandahåller en mall för klassen RNDIS och finns i usbx_windows_host_files-katalogen.</span><span class="sxs-lookup"><span data-stu-id="b7310-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="b7310-125">För senare versioner av Windows ska filen RNDIS_Template. inf användas.</span><span class="sxs-lookup"><span data-stu-id="b7310-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="b7310-126">Den här filen måste ändras för att återspegla det PID/VID som används av enheten.</span><span class="sxs-lookup"><span data-stu-id="b7310-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="b7310-127">PID/VID är specifika för den slutgiltiga kunden när företaget och produkten registreras med USB-IF.</span><span class="sxs-lookup"><span data-stu-id="b7310-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="b7310-128">I INF-filen finns fälten som ska ändras här.</span><span class="sxs-lookup"><span data-stu-id="b7310-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="b7310-129">I enhets ramverket för RNDIS-enheten lagras PID/VID i enhets beskrivningen (se den enhets beskrivning som anges ovan)</span><span class="sxs-lookup"><span data-stu-id="b7310-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="b7310-130">När ett USB-värdnamn identifierar USB-RNDIS enhet monteras ett nätverks gränssnitt och enheten kan användas med nätverks protokolls Tacken.</span><span class="sxs-lookup"><span data-stu-id="b7310-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="b7310-131">Se värd operativ systemet för referens.</span><span class="sxs-lookup"><span data-stu-id="b7310-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="b7310-132">DFU-klass för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="b7310-132">USB Device DFU Class</span></span>

<span data-ttu-id="b7310-133">USB-enhetens DFU-klass tillåter att ett USB-värdnamn uppdaterar enhetens inbyggda program vara baserat på ett värd program.</span><span class="sxs-lookup"><span data-stu-id="b7310-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="b7310-134">Klassen DFU är en USB-IF-standardklass.</span><span class="sxs-lookup"><span data-stu-id="b7310-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="b7310-135">USBX DFU-klassen är relativt enkel.</span><span class="sxs-lookup"><span data-stu-id="b7310-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="b7310-136">IT-enhetens Beskrivning kräver inte något annat än en kontroll slut punkt.</span><span class="sxs-lookup"><span data-stu-id="b7310-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="b7310-137">I de flesta fall kommer den här klassen att bäddas in i en USB-sammansatt enhet.</span><span class="sxs-lookup"><span data-stu-id="b7310-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="b7310-138">Enheten kan vara något som en lagrings enhet eller en kommunikations enhet och det tillagda DFU-gränssnittet kan informera värden om att enheten kan uppdatera sin inbyggda program vara i farten.</span><span class="sxs-lookup"><span data-stu-id="b7310-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="b7310-139">DFU-klassen fungerar i tre steg.</span><span class="sxs-lookup"><span data-stu-id="b7310-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="b7310-140">Första enheten monteras som normal med den exporterade klassen.</span><span class="sxs-lookup"><span data-stu-id="b7310-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="b7310-141">Ett program på värden (Windows eller Linux) kommer att utnyttja klassen DFU och skicka en begäran om att återställa enheten till DFU-läge.</span><span class="sxs-lookup"><span data-stu-id="b7310-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="b7310-142">Enheten kommer att försvinna från bussen under en kort tid (tillräckligt för värden och enheten för att identifiera en återställnings ordning) och vid omstart är enheten exklusivt i DFU-läge, väntar på att värd programmet ska skicka en uppgradering av inbyggd program vara.</span><span class="sxs-lookup"><span data-stu-id="b7310-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="b7310-143">När uppgraderingen av den inbyggda program varan har slutförts återställer värd programmet enheten och när den omräknas igen återgår enheten till sin normala drift med den nya inbyggda program varan.</span><span class="sxs-lookup"><span data-stu-id="b7310-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="b7310-144">En DFU Device Framework ser ut så här.</span><span class="sxs-lookup"><span data-stu-id="b7310-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="b7310-145">I det här exemplet är DFU-beskrivningen inte associerad med några andra klasser.</span><span class="sxs-lookup"><span data-stu-id="b7310-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="b7310-146">Den har en enkel gränssnitts beskrivning och inga andra slut punkter är kopplade till den.</span><span class="sxs-lookup"><span data-stu-id="b7310-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="b7310-147">Det finns en funktions beskrivning som beskriver de olika DFU-funktionerna på enheten.</span><span class="sxs-lookup"><span data-stu-id="b7310-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="b7310-148">Beskrivningen av DFU-funktionerna är följande.</span><span class="sxs-lookup"><span data-stu-id="b7310-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="b7310-149">Name</span><span class="sxs-lookup"><span data-stu-id="b7310-149">Name</span></span>             | <span data-ttu-id="b7310-150">Offset</span><span class="sxs-lookup"><span data-stu-id="b7310-150">Offset</span></span>  | <span data-ttu-id="b7310-151">Storlek</span><span class="sxs-lookup"><span data-stu-id="b7310-151">Size</span></span> | <span data-ttu-id="b7310-152">typ</span><span class="sxs-lookup"><span data-stu-id="b7310-152">type</span></span>      | <span data-ttu-id="b7310-153">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="b7310-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="b7310-154">bmAttributes</span></span>  | <span data-ttu-id="b7310-155">2</span><span class="sxs-lookup"><span data-stu-id="b7310-155">2</span></span>     | <span data-ttu-id="b7310-156">1</span><span class="sxs-lookup"><span data-stu-id="b7310-156">1</span></span>   | <span data-ttu-id="b7310-157">Bitars fält</span><span class="sxs-lookup"><span data-stu-id="b7310-157">Bit field</span></span> | <span data-ttu-id="b7310-158">Bit 3: enheten utför en buss-koppla bort sekvens när den får en DFU_DETACH begäran.</span><span class="sxs-lookup"><span data-stu-id="b7310-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="b7310-159">Värden får inte utfärda en USB-återställning.</span><span class="sxs-lookup"><span data-stu-id="b7310-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="b7310-160">(bitWillDetach) 0 = ingen 1 = Yes bit 2: enheten kan kommunicera via USB efter manifest fasen.</span><span class="sxs-lookup"><span data-stu-id="b7310-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="b7310-161">(bitManifestationTolerant) 0 = Nej, måste se buss återställning 1 = Ja bit 1: uppladdnings funktion (bitCanUpload) 0 = ingen 1 = Yes bit 0: nedladdnings bar funktion (bitCanDnload) 0 = ingen 1 = Ja</span><span class="sxs-lookup"><span data-stu-id="b7310-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="b7310-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="b7310-162">wDetachTimeOut</span></span>  | <span data-ttu-id="b7310-163">3</span><span class="sxs-lookup"><span data-stu-id="b7310-163">3</span></span>      | <span data-ttu-id="b7310-164">2</span><span class="sxs-lookup"><span data-stu-id="b7310-164">2</span></span>  | <span data-ttu-id="b7310-165">antal</span><span class="sxs-lookup"><span data-stu-id="b7310-165">number</span></span>    | <span data-ttu-id="b7310-166">Tid i millisekunder som enheten väntar efter att DFU_DETACH-begäran har mottagits.</span><span class="sxs-lookup"><span data-stu-id="b7310-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="b7310-167">Om den här tiden går ut utan en USB-återställning avslutar enheten omkonfigurations fasen och återgår till normal drift.</span><span class="sxs-lookup"><span data-stu-id="b7310-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="b7310-168">Detta motsvarar den längsta tid som enheten kan vänta (beroende på dess timers, osv.).</span><span class="sxs-lookup"><span data-stu-id="b7310-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="b7310-169">USBX anger det här värdet till 1000 MS.</span><span class="sxs-lookup"><span data-stu-id="b7310-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="b7310-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="b7310-170">wTransferSize</span></span>  | <span data-ttu-id="b7310-171">5</span><span class="sxs-lookup"><span data-stu-id="b7310-171">5</span></span>      | <span data-ttu-id="b7310-172">2</span><span class="sxs-lookup"><span data-stu-id="b7310-172">2</span></span>  | <span data-ttu-id="b7310-173">antal</span><span class="sxs-lookup"><span data-stu-id="b7310-173">number</span></span>    | <span data-ttu-id="b7310-174">Maximalt antal byte som enheten kan godkänna vid \- Skriv åtgärd per kontroll.</span><span class="sxs-lookup"><span data-stu-id="b7310-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="b7310-175">USBX anger det här värdet till 64 byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="b7310-176">DFU-klassens deklaration är följande:</span><span class="sxs-lookup"><span data-stu-id="b7310-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="b7310-177">DFU-klassen måste fungera med en enhets program vara som är specifik för målet.</span><span class="sxs-lookup"><span data-stu-id="b7310-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="b7310-178">Därför definierar den flera anrop tillbaka till Läs-och skriv block med inbyggd program vara och hämta status från uppdaterings programmet för den inbyggda program varan.</span><span class="sxs-lookup"><span data-stu-id="b7310-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="b7310-179">Klassen DFU har också en funktion för att uppmana dig att meddela programmet när den inbyggda program varans start och slut har överförts.</span><span class="sxs-lookup"><span data-stu-id="b7310-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="b7310-180">Nedan visas en beskrivning av ett typiskt DFU-programflöde.</span><span class="sxs-lookup"><span data-stu-id="b7310-180">Following is the description of a typical DFU application flow.</span></span>

![DFU program flöde](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="b7310-182">Den största utmaningen i DFU-klassen får rätt program på värden för att utföra hämtningen av den inbyggda program varan.</span><span class="sxs-lookup"><span data-stu-id="b7310-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="b7310-183">Det finns inget program från Microsoft eller USB-IF.</span><span class="sxs-lookup"><span data-stu-id="b7310-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="b7310-184">Vissa shareware finns och de fungerar bra på Linux och i mindre utsträckning i Windows.</span><span class="sxs-lookup"><span data-stu-id="b7310-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="b7310-185">I Linux finns en DFU-utils som du kan hitta här: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) mycket information om DFU-utils finns också på den här länken: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span><span class="sxs-lookup"><span data-stu-id="b7310-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="b7310-186">Linux-implementeringen av DFU utför korrekt återställnings ordningen mellan värden och enheten och därför behöver enheten inte göra det.</span><span class="sxs-lookup"><span data-stu-id="b7310-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="b7310-187">Linux kan godkänna bmAttributes- *bitWillDetach* till 0.</span><span class="sxs-lookup"><span data-stu-id="b7310-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="b7310-188">Windows på den andra sidan kräver att enheten utför återställningen.</span><span class="sxs-lookup"><span data-stu-id="b7310-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="b7310-189">I Windows måste USB-registret kunna associera USB-enheten med sitt PID/VID och USB-biblioteket som i sin tur används av DFU-programmet.</span><span class="sxs-lookup"><span data-stu-id="b7310-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="b7310-190">Detta kan vara enkelt att göra med den kostnads fria Zadig som du hittar här: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .</span><span class="sxs-lookup"><span data-stu-id="b7310-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="b7310-191">När du kör Zadig för första gången visas den här skärmen:</span><span class="sxs-lookup"><span data-stu-id="b7310-191">Running Zadig for the first time will show this screen:</span></span>

![Kör Zadig för första gången](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="b7310-193">I enhets listan letar du reda på din enhet och associerar den med libusb Windows-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="b7310-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="b7310-194">Detta binder enhets numret/VID enheten med Windows USB-biblioteket som används av DFU-verktygen.</span><span class="sxs-lookup"><span data-stu-id="b7310-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="b7310-195">Om du vill använda kommandot DFU packar du upp de zippade DFU-verktygen i en katalog och kontrollerar att libusb-DLL-filen också finns i samma katalog.</span><span class="sxs-lookup"><span data-stu-id="b7310-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="b7310-196">DFU-verktygen måste köras från en DOS-ruta på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b7310-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="b7310-197">Börja med att skriva kommandot **DFU-util – l** för att avgöra om enheten visas i listan.</span><span class="sxs-lookup"><span data-stu-id="b7310-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="b7310-198">Om inte kör du Zadig för att kontrol lera att enheten är listad och kopplad till USB-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="b7310-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="b7310-199">Du bör se en skärm på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="b7310-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="b7310-200">Nästa steg är att förbereda filen som ska laddas ned.</span><span class="sxs-lookup"><span data-stu-id="b7310-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="b7310-201">USBX DFU-klassen utför ingen verifiering på den här filen och är oberoende av dess interna format.</span><span class="sxs-lookup"><span data-stu-id="b7310-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="b7310-202">Den här inbyggda program varan är särskilt speciell för målet men inte att DFU eller USBX.</span><span class="sxs-lookup"><span data-stu-id="b7310-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="b7310-203">Sedan kan DFU-util instrueras att skicka filen genom att skriva följande kommando:</span><span class="sxs-lookup"><span data-stu-id="b7310-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="b7310-204">DFU-util bör Visa fil hämtnings processen tills den inbyggda program varan har laddats ned helt.</span><span class="sxs-lookup"><span data-stu-id="b7310-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="b7310-205">PIMA-klass (PTP-svarare) för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="b7310-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="b7310-206">USB-enhetens PIMA-klass tillåter att ett USB-värdnamn (Initiator) ansluter till en</span><span class="sxs-lookup"><span data-stu-id="b7310-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="b7310-207">PIMA-enhet (Resonder) för överföring av mediafiler.</span><span class="sxs-lookup"><span data-stu-id="b7310-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="b7310-208">USBX Pima-klassen överensstämmer med USB-IF PIMA 15740-klassen kallas även PTP-klass (för Picture Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="b7310-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="b7310-209">USBX PIMA-klassen stöder följande åtgärder.</span><span class="sxs-lookup"><span data-stu-id="b7310-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="b7310-210">Åtgärds kod</span><span class="sxs-lookup"><span data-stu-id="b7310-210">Operation code</span></span>                                    | <span data-ttu-id="b7310-211">Värde</span><span class="sxs-lookup"><span data-stu-id="b7310-211">Value</span></span> | <span data-ttu-id="b7310-212">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="b7310-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="b7310-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="b7310-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="b7310-214">0x1001</span></span>  | <span data-ttu-id="b7310-215">Hämta de åtgärder och händelser som stöds av enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="b7310-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="b7310-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="b7310-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="b7310-217">0x1002</span></span>  | <span data-ttu-id="b7310-218">Öppna en session mellan värden och enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="b7310-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="b7310-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="b7310-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="b7310-220">0x1003</span></span>  | <span data-ttu-id="b7310-221">Stäng en session mellan värden och enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="b7310-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="b7310-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="b7310-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="b7310-223">0x1004</span></span>  | <span data-ttu-id="b7310-224">Returnerar enhetens lagrings-ID.</span><span class="sxs-lookup"><span data-stu-id="b7310-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="b7310-225">USBX PIMA använder bara ett lagrings-ID</span><span class="sxs-lookup"><span data-stu-id="b7310-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="b7310-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="b7310-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="b7310-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="b7310-227">0x1005</span></span>  | <span data-ttu-id="b7310-228">Returnera information om lagrings objekt såsom maximal kapacitet och ledigt utrymme</span><span class="sxs-lookup"><span data-stu-id="b7310-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="b7310-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="b7310-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="b7310-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="b7310-230">0x1006</span></span>  | <span data-ttu-id="b7310-231">Returnera antalet objekt som finns i lagrings enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="b7310-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="b7310-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="b7310-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="b7310-233">0x1007</span></span>  | <span data-ttu-id="b7310-234">Returnera en matris med referenser för objekten på lagrings enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="b7310-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="b7310-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="b7310-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="b7310-236">0x1008</span></span>  | <span data-ttu-id="b7310-237">Returnera information om ett objekt, till exempel namnet på objektet, dess skapelse datum, ändrings datum</span><span class="sxs-lookup"><span data-stu-id="b7310-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="b7310-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="b7310-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="b7310-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="b7310-239">0x1009</span></span>  | <span data-ttu-id="b7310-240">Returnera data som hör till ett angivet objekt</span><span class="sxs-lookup"><span data-stu-id="b7310-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="b7310-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="b7310-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="b7310-242">0x100A</span><span class="sxs-lookup"><span data-stu-id="b7310-242">0x100A</span></span>  | <span data-ttu-id="b7310-243">Skicka miniatyren om den är tillgänglig för ett objekt</span><span class="sxs-lookup"><span data-stu-id="b7310-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="b7310-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="b7310-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="b7310-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="b7310-245">0x100B</span></span>  | <span data-ttu-id="b7310-246">Ta bort ett objekt på mediet</span><span class="sxs-lookup"><span data-stu-id="b7310-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="b7310-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="b7310-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="b7310-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="b7310-248">0x100C</span></span>  | <span data-ttu-id="b7310-249">Skicka till enhets informationen om ett objekt för att skapa det på mediet</span><span class="sxs-lookup"><span data-stu-id="b7310-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="b7310-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="b7310-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="b7310-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="b7310-251">0x100D</span></span>  | <span data-ttu-id="b7310-252">Skicka data för ett objekt till enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="b7310-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="b7310-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="b7310-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="b7310-254">0x100F</span></span>  | <span data-ttu-id="b7310-255">Rengör enhets mediet</span><span class="sxs-lookup"><span data-stu-id="b7310-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="b7310-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="b7310-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="b7310-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="b7310-257">0x0110</span></span>  | <span data-ttu-id="b7310-258">Återställa mål enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="b7310-259">Åtgärds kod</span><span class="sxs-lookup"><span data-stu-id="b7310-259">Operation Code</span></span>                                         | <span data-ttu-id="b7310-260">Värde</span><span class="sxs-lookup"><span data-stu-id="b7310-260">Value</span></span> | <span data-ttu-id="b7310-261">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="b7310-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="b7310-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="b7310-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="b7310-263">0x4001</span></span>  | <span data-ttu-id="b7310-264">Avbryter den aktuella transaktionen</span><span class="sxs-lookup"><span data-stu-id="b7310-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="b7310-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="b7310-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="b7310-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="b7310-266">0x4002</span></span>  | <span data-ttu-id="b7310-267">Ett objekt har lagts till i enhets mediet och kan hämtas av host\.</span><span class="sxs-lookup"><span data-stu-id="b7310-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="b7310-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="b7310-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="b7310-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="b7310-269">0x4003</span></span>  | <span data-ttu-id="b7310-270">Ett objekt har tagits bort från enhets mediet</span><span class="sxs-lookup"><span data-stu-id="b7310-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="b7310-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="b7310-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="b7310-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="b7310-272">0x4004</span></span>  | <span data-ttu-id="b7310-273">Ett medium har lagts till i enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="b7310-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="b7310-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="b7310-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="b7310-275">0x4005</span></span>  | <span data-ttu-id="b7310-276">Ett medium har tagits bort från enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="b7310-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="b7310-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="b7310-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="b7310-278">0x4006</span></span>  | <span data-ttu-id="b7310-279">Enhets egenskaperna har ändrats</span><span class="sxs-lookup"><span data-stu-id="b7310-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="b7310-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="b7310-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="b7310-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="b7310-281">0x4007</span></span>  | <span data-ttu-id="b7310-282">En objekt information har ändrats</span><span class="sxs-lookup"><span data-stu-id="b7310-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="b7310-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="b7310-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="b7310-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="b7310-284">0x4008</span></span>  | <span data-ttu-id="b7310-285">En enhet har ändrats</span><span class="sxs-lookup"><span data-stu-id="b7310-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="b7310-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="b7310-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="b7310-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="b7310-287">0x4009</span></span>  | <span data-ttu-id="b7310-288">Enheten begär överföring av ett objekt från värden</span><span class="sxs-lookup"><span data-stu-id="b7310-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="b7310-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="b7310-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="b7310-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="b7310-290">0x400A</span></span>  | <span data-ttu-id="b7310-291">Enheten rapporterar att mediet är fullt</span><span class="sxs-lookup"><span data-stu-id="b7310-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="b7310-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="b7310-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="b7310-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="b7310-293">0x400B</span></span>  | <span data-ttu-id="b7310-294">Enhets rapporter som den återställdes</span><span class="sxs-lookup"><span data-stu-id="b7310-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="b7310-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="b7310-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="b7310-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="b7310-296">0x400C</span></span>  | <span data-ttu-id="b7310-297">Lagrings information har ändrats på enheten</span><span class="sxs-lookup"><span data-stu-id="b7310-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="b7310-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="b7310-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="b7310-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="b7310-299">0x400D</span></span>  | <span data-ttu-id="b7310-300">Avbildningen har slutförts</span><span class="sxs-lookup"><span data-stu-id="b7310-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="b7310-301">Enhets klassen USBX PIMA använder en TX-tråd för att lyssna på PIMA-kommandon från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="b7310-302">Ett PIMA-kommando består av ett kommando block, ett data block och en status fas.</span><span class="sxs-lookup"><span data-stu-id="b7310-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="b7310-303">Funktionen ux_device_class_pima_thread publicerar en begäran till stacken för att ta emot ett PIMA-kommando från värd sidan.</span><span class="sxs-lookup"><span data-stu-id="b7310-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="b7310-304">PIMA-kommandot avkodas och verifieras för innehåll.</span><span class="sxs-lookup"><span data-stu-id="b7310-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="b7310-305">Om kommando blocket är giltigt är det grenat till lämplig kommando hanterare.</span><span class="sxs-lookup"><span data-stu-id="b7310-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="b7310-306">De flesta PIMA-kommandon kan bara utföras när en session har öppnats av värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="b7310-307">Det enda undantaget är kommandot **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span><span class="sxs-lookup"><span data-stu-id="b7310-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="b7310-308">Med USBX PIMA-implementeringen kan endast en session öppnas mellan en initierare och en svarare när som helst.</span><span class="sxs-lookup"><span data-stu-id="b7310-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="b7310-309">Alla transaktioner i den enskilda sessionen blockeras och ingen ny transaktion kan börja innan den tidigare slutförts.</span><span class="sxs-lookup"><span data-stu-id="b7310-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="b7310-310">PIMA-transaktioner består av tre faser, en kommando fas, en valfri data fas och en svars fas.</span><span class="sxs-lookup"><span data-stu-id="b7310-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="b7310-311">Om det finns en data fas kan den bara vara i en riktning.</span><span class="sxs-lookup"><span data-stu-id="b7310-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="b7310-312">Initieraren fastställer alltid flödet för PIMA-åtgärder, men den som svarar kan initiera händelser tillbaka till initieraren för att informera om status ändringar som har skett under en session.</span><span class="sxs-lookup"><span data-stu-id="b7310-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="b7310-313">Följande diagram visar överföringen av ett data objekt mellan värden och enhets klassen PIMA.</span><span class="sxs-lookup"><span data-stu-id="b7310-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![PIMA transaktioner](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="b7310-315">Initiering av enhets klassen PIMA</span><span class="sxs-lookup"><span data-stu-id="b7310-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="b7310-316">PIMA enhets klass behöver vissa parametrar som tillhandahålls av programmet under initieringen.</span><span class="sxs-lookup"><span data-stu-id="b7310-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="b7310-317">Följande parametrar beskriver enhets-och lagrings information.</span><span class="sxs-lookup"><span data-stu-id="b7310-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="b7310-318">PIMA-klassen kräver också registrering av motringning till programmet för att informera om tillämpningen av vissa händelser eller hämta/lagra data från/till det lokala mediet.</span><span class="sxs-lookup"><span data-stu-id="b7310-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="b7310-319">Återanropen är följande.</span><span class="sxs-lookup"><span data-stu-id="b7310-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="b7310-320">I följande exempel visas hur du initierar klient sidan av PIMA.</span><span class="sxs-lookup"><span data-stu-id="b7310-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="b7310-321">I det här exemplet används PictBridge som en klient för PIMA.</span><span class="sxs-lookup"><span data-stu-id="b7310-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="b7310-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="b7310-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="b7310-323">Lägga till ett objekt och skicka händelsen till värden</span><span class="sxs-lookup"><span data-stu-id="b7310-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-324">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="b7310-325">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-325">Description</span></span>

<span data-ttu-id="b7310-326">Den här funktionen anropas när PIMA-klassen behöver lägga till ett objekt och informera värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-327">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-327">Parameters</span></span>

- <span data-ttu-id="b7310-328">**Pima**: pekar mot Pima-klass instansen</span><span class="sxs-lookup"><span data-stu-id="b7310-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="b7310-329">**object_handle**: objektets handtag.</span><span class="sxs-lookup"><span data-stu-id="b7310-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="b7310-330">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="b7310-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="b7310-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="b7310-332">Hämtar objekt numret från programmet</span><span class="sxs-lookup"><span data-stu-id="b7310-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="b7310-334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-334">Description</span></span>

<span data-ttu-id="b7310-335">Den här funktionen anropas när PIMA-klassen behöver hämta antalet objekt i det lokala systemet och skicka tillbaka den till värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-336">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-336">Parameters</span></span>

- <span data-ttu-id="b7310-337">**Pima**: pekar mot Pima-klass instansen</span><span class="sxs-lookup"><span data-stu-id="b7310-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="b7310-338">**object_number**: adressen för det antal objekt som ska returneras</span><span class="sxs-lookup"><span data-stu-id="b7310-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="b7310-339">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="b7310-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="b7310-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="b7310-341">Returnera objektets referens mat ris</span><span class="sxs-lookup"><span data-stu-id="b7310-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-342">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="b7310-343">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-343">Description</span></span>

<span data-ttu-id="b7310-344">Den här funktionen anropas när PIMA-klassen behöver hämta objektet hanterar matrisen i det lokala systemet och skicka tillbaka den till värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-345">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-345">Parameters</span></span>

- <span data-ttu-id="b7310-346">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b7310-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b7310-347">**object_handles_format_code**: format kod för handtagen</span><span class="sxs-lookup"><span data-stu-id="b7310-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="b7310-348">**object_handles_association**: objekt kopplings kod</span><span class="sxs-lookup"><span data-stu-id="b7310-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="b7310-349">**object_handle_array**: adress dit du vill lagra handtagen</span><span class="sxs-lookup"><span data-stu-id="b7310-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="b7310-350">**object_handles_max_number**: högsta antal referenser i matrisen</span><span class="sxs-lookup"><span data-stu-id="b7310-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="b7310-351">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="b7310-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="b7310-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="b7310-353">Returnera objekt informationen</span><span class="sxs-lookup"><span data-stu-id="b7310-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-354">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="b7310-355">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-355">Description</span></span>

<span data-ttu-id="b7310-356">Den här funktionen anropas när PIMA-klassen behöver hämta objektet hanterar matrisen i det lokala systemet och skicka tillbaka den till värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-357">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-357">Parameters</span></span>

- <span data-ttu-id="b7310-358">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b7310-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b7310-359">**object_handles**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b7310-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="b7310-360">**objekt**: objektets pekare adress</span><span class="sxs-lookup"><span data-stu-id="b7310-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="b7310-361">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="b7310-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="b7310-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="b7310-363">Returnera objekt data</span><span class="sxs-lookup"><span data-stu-id="b7310-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-364">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="b7310-365">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-365">Description</span></span>

<span data-ttu-id="b7310-366">Den här funktionen anropas när PIMA-klassen behöver hämta objekt data i det lokala systemet och skicka tillbaka den till värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-367">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-367">Parameters</span></span>

- <span data-ttu-id="b7310-368">**Pima**: pekar mot instans av Pima-klassen.</span><span class="sxs-lookup"><span data-stu-id="b7310-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="b7310-369">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b7310-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="b7310-370">**object_buffer**: objektets bufferts adress</span><span class="sxs-lookup"><span data-stu-id="b7310-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="b7310-371">**object_length_requested**: den objekt data längd som klienten har begärt till programmet</span><span class="sxs-lookup"><span data-stu-id="b7310-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="b7310-372">**object_actual_length**: objekt data längden som returnerades av programmet</span><span class="sxs-lookup"><span data-stu-id="b7310-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="b7310-373">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="b7310-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="b7310-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="b7310-375">Värd skickar objekt informationen</span><span class="sxs-lookup"><span data-stu-id="b7310-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-376">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="b7310-377">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-377">Description</span></span>

<span data-ttu-id="b7310-378">Den här funktionen anropas när PIMA-klassen behöver ta emot objekt informationen i det lokala systemet för framtida lagring.</span><span class="sxs-lookup"><span data-stu-id="b7310-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-379">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-379">Parameters</span></span>

- <span data-ttu-id="b7310-380">**Pima**: pekar mot Pima-klass instansen</span><span class="sxs-lookup"><span data-stu-id="b7310-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="b7310-381">**objekt**: pekar mot objektet</span><span class="sxs-lookup"><span data-stu-id="b7310-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="b7310-382">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b7310-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="b7310-383">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="b7310-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="b7310-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="b7310-385">Värden skickar objekt data</span><span class="sxs-lookup"><span data-stu-id="b7310-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-386">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="b7310-387">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-387">Description</span></span>

<span data-ttu-id="b7310-388">Den här funktionen anropas när PIMA-klassen behöver ta emot objekt data i det lokala systemet för lagring.</span><span class="sxs-lookup"><span data-stu-id="b7310-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-389">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-389">Parameters</span></span>

- <span data-ttu-id="b7310-390">**Pima**: pekar mot Pima-klass instansen</span><span class="sxs-lookup"><span data-stu-id="b7310-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="b7310-391">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b7310-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="b7310-392">**fas**: överförings fasen (aktiv eller fullständig)</span><span class="sxs-lookup"><span data-stu-id="b7310-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="b7310-393">**object_buffer**: objektets bufferts adress</span><span class="sxs-lookup"><span data-stu-id="b7310-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="b7310-394">**object_offset**: data adress</span><span class="sxs-lookup"><span data-stu-id="b7310-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="b7310-395">**object_length**: objekt data längden har skickats av programmet</span><span class="sxs-lookup"><span data-stu-id="b7310-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="b7310-396">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="b7310-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="b7310-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="b7310-398">Ta bort ett lokalt objekt</span><span class="sxs-lookup"><span data-stu-id="b7310-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-399">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="b7310-400">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-400">Description</span></span>

<span data-ttu-id="b7310-401">Den här funktionen anropas när PIMA-klassen behöver ta bort ett objekt i den lokala lagringen.</span><span class="sxs-lookup"><span data-stu-id="b7310-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-402">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-402">Parameters</span></span>

- <span data-ttu-id="b7310-403">**Pima**: pekar mot Pima-klass instansen</span><span class="sxs-lookup"><span data-stu-id="b7310-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="b7310-404">**object_handle**: referens för objektet</span><span class="sxs-lookup"><span data-stu-id="b7310-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="b7310-405">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="b7310-406">Ljud klass för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="b7310-406">USB Device Audio Class</span></span>

<span data-ttu-id="b7310-407">Ljud klassen USB-enhet gör att ett USB-värdnamn kan kommunicera med enheten som en ljuden het.</span><span class="sxs-lookup"><span data-stu-id="b7310-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="b7310-408">Den här klassen baseras på USB-standarden och USB Audio-klassen 1,0 eller 2,0 standard.</span><span class="sxs-lookup"><span data-stu-id="b7310-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="b7310-409">En USB-kompatibel enhets ramverk måste deklareras av enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="b7310-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="b7310-410">Ett exempel på en ljud 2,0-talare följer:</span><span class="sxs-lookup"><span data-stu-id="b7310-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="b7310-411">Klassen Audio använder ett sammansatt enhets ramverk för att gruppera gränssnitt (kontroll och strömning).</span><span class="sxs-lookup"><span data-stu-id="b7310-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="b7310-412">Därför bör du vidta åtgärder när du definierar enhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="b7310-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="b7310-413">USBX förlitar sig på IAD-beskrivningen för att veta internt hur man binder gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="b7310-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="b7310-414">IAD-beskrivningen måste deklareras före gränssnitten (ett AudioControl-gränssnitt följt av ett eller flera AudioStreaming-gränssnitt) och innehålla det första gränssnittet i klassen Audio (AudioControl-gränssnittet) och hur många gränssnitt som är kopplade.</span><span class="sxs-lookup"><span data-stu-id="b7310-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="b7310-415">Hur klassen Audio fungerar beror på om enheten skickar eller tar emot ljud, men båda fallen använder en FIFO för att lagra ljud Rams buffertar: om enheten skickar ljud till värden, lägger programmet till ljud Rams buffertar till FIFO som senare skickas till värden av USBX; Om enheten tar emot ljud från värden lägger USBX till de ljud Rams buffertar som tas emot från värden till FIFO-enheten som senare läses av programmet.</span><span class="sxs-lookup"><span data-stu-id="b7310-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="b7310-416">Varje ljud ström har en egen FIFO, och varje buffert för ljud ramar består av flera exempel.</span><span class="sxs-lookup"><span data-stu-id="b7310-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="b7310-417">Initieringen av klassen Audio förväntar sig följande delar.</span><span class="sxs-lookup"><span data-stu-id="b7310-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="b7310-418">Klassen Audio förväntar sig följande strömnings parametrar:</span><span class="sxs-lookup"><span data-stu-id="b7310-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="b7310-419">Klassen Audio förväntar sig följande funktions parametrar.</span><span class="sxs-lookup"><span data-stu-id="b7310-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="b7310-420">Den programdefinierade kontrollen begär motringning (***ux_device_class_audio_control_process***; som anges i föregående exempel) anropas när stacken tar emot en kontrollbegäran från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="b7310-421">Om begäran godkänns och hanteras (bekräftas eller stoppas) måste återanropet returnera ett fel, annars ska felet returneras.</span><span class="sxs-lookup"><span data-stu-id="b7310-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="b7310-422">Den klassbaserade kontrollen begär processen definieras som en programdefinierad motringning eftersom kontroll förfrågningarna är mycket olika mellan USB-ljudversioner och en stor del av processen för begäran relaterar till enhets ramverket.</span><span class="sxs-lookup"><span data-stu-id="b7310-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="b7310-423">Programmet ska hantera begär Anden korrekt för att enheten ska fungera.</span><span class="sxs-lookup"><span data-stu-id="b7310-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="b7310-424">Eftersom en ljuden het, volym, ljud av och samplings frekvens är vanliga kontroll begär Anden, är det enkelt att använda internt definierade återanrop för olika versioner av USB-ljud i senare avsnitt för program som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b7310-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="b7310-425">Se ***ux_device_class_audio10_control_process** _ och _ *_ux_device_class_audio_control_request_** för mer information.</span><span class="sxs-lookup"><span data-stu-id="b7310-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="b7310-426">I enhets ramverket för ljud enheten lagras PID/VID i enhets beskrivningen (se den enhets beskrivning som anges ovan).</span><span class="sxs-lookup"><span data-stu-id="b7310-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="b7310-427">När ett USB-värdnamn identifierar USB-ljudenheten och monterar klassen Audio, kan enheten användas med valfri ljuds pelare eller inspelning (beroende på ramverket).</span><span class="sxs-lookup"><span data-stu-id="b7310-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="b7310-428">Se värd operativ systemet för referens.</span><span class="sxs-lookup"><span data-stu-id="b7310-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="b7310-429">Ljud klassens API: er definieras nedan.</span><span class="sxs-lookup"><span data-stu-id="b7310-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="b7310-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="b7310-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="b7310-431">Tråd inmatning för läsning av data för ljud funktionen.</span><span class="sxs-lookup"><span data-stu-id="b7310-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-432">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="b7310-433">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-433">Description</span></span>

<span data-ttu-id="b7310-434">Den här funktionen skickas till initierings parametern för ljud strömmen om du vill läsa ljud från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="b7310-435">Internt skapas en tråd med den här funktionen som dess post funktion. själva tråden läser ljud data genom den isokrona slut punkten i ljud funktionen.</span><span class="sxs-lookup"><span data-stu-id="b7310-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-436">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-436">Parameters</span></span>

- <span data-ttu-id="b7310-437">**audio_stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="b7310-438">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="b7310-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="b7310-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="b7310-440">Tråd inmatning för att skriva data för ljud funktionen</span><span class="sxs-lookup"><span data-stu-id="b7310-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-441">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="b7310-442">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-442">Description</span></span>

<span data-ttu-id="b7310-443">Den här funktionen skickas till initierings parametern för ljud strömmen om du vill skriva ljud till värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="b7310-444">Internt skapas en tråd med den här funktionen som dess post funktion. själva tråden skriver ljud data via den isokrona slut punkten i ljud funktionen.</span><span class="sxs-lookup"><span data-stu-id="b7310-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-445">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-445">Parameters</span></span>

- <span data-ttu-id="b7310-446">**audio_stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="b7310-447">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="b7310-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="b7310-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="b7310-449">Hämta en speciell Stream-instans för ljud funktionen</span><span class="sxs-lookup"><span data-stu-id="b7310-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-450">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="b7310-451">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-451">Description</span></span>

<span data-ttu-id="b7310-452">Den här funktionen används för att hämta en strömmande instans av klassen Audio.</span><span class="sxs-lookup"><span data-stu-id="b7310-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-453">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-453">Parameters</span></span>

- <span data-ttu-id="b7310-454">**ljud**: pekar mot ljud instansen</span><span class="sxs-lookup"><span data-stu-id="b7310-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="b7310-455">**stream_index**: Stream instance index baserat på 0</span><span class="sxs-lookup"><span data-stu-id="b7310-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="b7310-456">**Stream**: pekare till buffer för att lagra pekaren för ljud strömmens instans</span><span class="sxs-lookup"><span data-stu-id="b7310-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-457">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-457">Return Value</span></span>

- <span data-ttu-id="b7310-458">**UX_SUCCESS** (0X00) den här åtgärden lyckades</span><span class="sxs-lookup"><span data-stu-id="b7310-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="b7310-459">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-460">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="b7310-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="b7310-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="b7310-462">Starta mottagning av ljud data för ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-463">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="b7310-464">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-464">Description</span></span>

<span data-ttu-id="b7310-465">Den här funktionen används för att starta läsning av ljud data i ljud strömmar.</span><span class="sxs-lookup"><span data-stu-id="b7310-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-466">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-466">Parameters</span></span>

- <span data-ttu-id="b7310-467">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-468">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-468">Return Value</span></span>

- <span data-ttu-id="b7310-469">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-471">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är full.</span><span class="sxs-lookup"><span data-stu-id="b7310-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="b7310-472">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-473">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="b7310-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="b7310-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="b7310-475">Läs 8-bitars exempel från ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-476">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="b7310-477">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-477">Description</span></span>

<span data-ttu-id="b7310-478">Den här funktionen läser 8-bitars ljud exempel data från den angivna data strömmen.</span><span class="sxs-lookup"><span data-stu-id="b7310-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="b7310-479">Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten.</span><span class="sxs-lookup"><span data-stu-id="b7310-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="b7310-480">När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-481">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-481">Parameters</span></span>

- <span data-ttu-id="b7310-482">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-483">**Buffer**: pekar mot bufferten för att spara exempel-byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-484">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-484">Return Value</span></span>

- <span data-ttu-id="b7310-485">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-487">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-488">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-489">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="b7310-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="b7310-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="b7310-491">Läsa 16-bitars exempel från ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-492">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="b7310-493">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-493">Description</span></span>

<span data-ttu-id="b7310-494">Den här funktionen läser 16-bitars ljud exempel data från den angivna data strömmen.</span><span class="sxs-lookup"><span data-stu-id="b7310-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="b7310-495">Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten.</span><span class="sxs-lookup"><span data-stu-id="b7310-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="b7310-496">När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-497">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-497">Parameters</span></span>

- <span data-ttu-id="b7310-498">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-499">**Buffer**: pekare till bufferten för att spara 16-bitars exemplet.</span><span class="sxs-lookup"><span data-stu-id="b7310-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-500">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-500">Return Value</span></span>

- <span data-ttu-id="b7310-501">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-503">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-504">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-505">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="b7310-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="b7310-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="b7310-507">Läs 24-bitars exempel från ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-508">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="b7310-509">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-509">Description</span></span>

<span data-ttu-id="b7310-510">Den här funktionen läser 24-bitars ljud exempel data från den angivna data strömmen.</span><span class="sxs-lookup"><span data-stu-id="b7310-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="b7310-511">Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten.</span><span class="sxs-lookup"><span data-stu-id="b7310-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="b7310-512">När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-513">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-513">Parameters</span></span>

- <span data-ttu-id="b7310-514">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-515">**Buffer**: pekare till bufferten för att spara exemplet med tre byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-516">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-516">Return Value</span></span>

- <span data-ttu-id="b7310-517">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-519">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-520">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-521">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="b7310-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="b7310-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="b7310-523">Läs 32-bitars exempel från ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-524">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="b7310-525">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-525">Description</span></span>

<span data-ttu-id="b7310-526">Den här funktionen läser 32-bitars ljud exempel data från den angivna data strömmen.</span><span class="sxs-lookup"><span data-stu-id="b7310-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="b7310-527">Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten.</span><span class="sxs-lookup"><span data-stu-id="b7310-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="b7310-528">När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-529">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-529">Parameters</span></span>

- <span data-ttu-id="b7310-530">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-531">**Buffer**: pekar mot bufferten för att spara data för 4 byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-532">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-532">Return Value</span></span>

- <span data-ttu-id="b7310-533">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-535">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-536">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-537">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="b7310-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="b7310-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="b7310-539">Få åtkomst till ljud ramen i ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-540">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="b7310-541">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-541">Description</span></span>

<span data-ttu-id="b7310-542">Den här funktionen returnerar den första ljud Rams bufferten och dess längd i den angivna data strömens FIFO.</span><span class="sxs-lookup"><span data-stu-id="b7310-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="b7310-543">När programmet har behandlat data måste ux_device_class_audio_read_frame_free användas för att frigöra bildruteproportioner i FIFO.</span><span class="sxs-lookup"><span data-stu-id="b7310-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-544">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-544">Parameters</span></span>

- <span data-ttu-id="b7310-545">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-546">**frame_data**: pekar på data pekare för att returnera data pekaren i.</span><span class="sxs-lookup"><span data-stu-id="b7310-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="b7310-547">**frame_length**: pekare till buffer för att spara ram längden i antal byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-548">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-548">Return Value</span></span>

- <span data-ttu-id="b7310-549">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-551">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-552">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-553">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="b7310-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="b7310-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="b7310-555">Frigör en buffert i ljud fönstret i ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-556">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="b7310-557">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-557">Description</span></span>

<span data-ttu-id="b7310-558">Med den här funktionen frigörs ljud bildens buffert längst fram i den angivna data strömmens FIFO så att den kan ta emot data från värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-559">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-559">Parameters</span></span>

- <span data-ttu-id="b7310-560">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-561">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-561">Return Value</span></span>

- <span data-ttu-id="b7310-562">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-564">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-565">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-566">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="b7310-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="b7310-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="b7310-568">Starta ljud data överföring för ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-569">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="b7310-570">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-570">Description</span></span>

<span data-ttu-id="b7310-571">Den här funktionen används för att börja skicka ljud data som skrivits till FIFO i klassen Audio.</span><span class="sxs-lookup"><span data-stu-id="b7310-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-572">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-572">Parameters</span></span>

- <span data-ttu-id="b7310-573">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-574">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-574">Return Value</span></span>

- <span data-ttu-id="b7310-575">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-577">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.</span><span class="sxs-lookup"><span data-stu-id="b7310-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="b7310-578">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-579">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="b7310-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="b7310-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="b7310-581">Skriv en ljud bild ruta i ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-582">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="b7310-583">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-583">Description</span></span>

<span data-ttu-id="b7310-584">Den här funktionen skriver en ram till ljud strömmens FIFO.</span><span class="sxs-lookup"><span data-stu-id="b7310-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="b7310-585">Ramdata kopieras till den tillgängliga bufferten i FIFO så att den kan skickas till värden.</span><span class="sxs-lookup"><span data-stu-id="b7310-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-586">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-586">Parameters</span></span>

- <span data-ttu-id="b7310-587">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-588">**ram**: pekar mot ramdata.</span><span class="sxs-lookup"><span data-stu-id="b7310-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="b7310-589">**frame_length** Ram längd i antal byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-590">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-590">Return Value</span></span>

- <span data-ttu-id="b7310-591">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-593">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är full.</span><span class="sxs-lookup"><span data-stu-id="b7310-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="b7310-594">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-595">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="b7310-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="b7310-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="b7310-597">Få åtkomst till ljud ramen i ljud strömmen</span><span class="sxs-lookup"><span data-stu-id="b7310-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-598">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="b7310-599">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-599">Description</span></span>

<span data-ttu-id="b7310-600">Den här funktionen hämtar adressen till den senaste ljud bildens buffert i FIFOn. den hämtar också längden på ljud Rams bufferten.</span><span class="sxs-lookup"><span data-stu-id="b7310-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="b7310-601">När programmet har fyllt i ljud fönstrets buffert med önskade data, måste ***ux_device_class_audio_write_frame_commit*** användas för att lägga till/bekräfta RAMSIDAN till FIFO.</span><span class="sxs-lookup"><span data-stu-id="b7310-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-602">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-602">Parameters</span></span>

- <span data-ttu-id="b7310-603">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-604">**frame_data**: pekar mot bildruta-datapekare för att returnera ramens data pekare i.</span><span class="sxs-lookup"><span data-stu-id="b7310-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="b7310-605">**frame_length** Pekar på bufferten för att spara ram längden i antal byte.</span><span class="sxs-lookup"><span data-stu-id="b7310-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-606">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-606">Return Value</span></span>

- <span data-ttu-id="b7310-607">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-609">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är full.</span><span class="sxs-lookup"><span data-stu-id="b7310-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="b7310-610">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-611">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="b7310-612">ux_device_class_audio_write_frame_commit</span><span class="sxs-lookup"><span data-stu-id="b7310-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="b7310-613">Bekräfta en buffert för ljud ramar i ljud strömmen.</span><span class="sxs-lookup"><span data-stu-id="b7310-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-614">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="b7310-615">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-615">Description</span></span>

<span data-ttu-id="b7310-616">Den här funktionen lägger till/aktiverar den senaste ljud bildens buffert till FIFO så att bufferten kan överföras till värden. Observera att den sista bufferten för ljud ramar borde ha fyllts i via ux_device_class_write_frame_get.</span><span class="sxs-lookup"><span data-stu-id="b7310-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-617">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-617">Parameters</span></span>

- <span data-ttu-id="b7310-618">**Stream**: pekar mot ljud Ströms instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="b7310-619">**längd**: antal byte som är klara i bufferten.</span><span class="sxs-lookup"><span data-stu-id="b7310-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-620">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-620">Return Value</span></span>

- <span data-ttu-id="b7310-621">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.</span><span class="sxs-lookup"><span data-stu-id="b7310-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="b7310-623">**UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är fssull.</span><span class="sxs-lookup"><span data-stu-id="b7310-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="b7310-624">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-625">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="b7310-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="b7310-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="b7310-627">Bearbeta USB-ljud 1,0-kontroll begär Anden</span><span class="sxs-lookup"><span data-stu-id="b7310-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-628">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="b7310-629">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-629">Description</span></span>

<span data-ttu-id="b7310-630">Den här funktionen hanterar grundläggande förfrågningar som skickas av värden på kontrollens slut punkt med en USB-ljud1,0-typ.</span><span class="sxs-lookup"><span data-stu-id="b7310-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="b7310-631">Ljud 1,0 funktioner för volym-och ljud uppspelnings förfrågningar bearbetas i funktionen.</span><span class="sxs-lookup"><span data-stu-id="b7310-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="b7310-632">När begär Anden bearbetas används fördefinierade data som skickas av den senaste parametern (grupp) för att besvara begär Anden och spara kontroll ändringar.</span><span class="sxs-lookup"><span data-stu-id="b7310-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-633">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-633">Parameters</span></span>

- <span data-ttu-id="b7310-634">**ljud**: pekar mot ljud instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="b7310-635">**överföring**: pekar mot överförings begär ande instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="b7310-636">**grupp**: data grupp för process för begäran.</span><span class="sxs-lookup"><span data-stu-id="b7310-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-637">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-637">Return Value</span></span>

- <span data-ttu-id="b7310-638">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-639">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-640">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="b7310-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="b7310-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="b7310-642">Bearbeta USB-ljud 1,0-kontroll begär Anden</span><span class="sxs-lookup"><span data-stu-id="b7310-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="b7310-643">Prototyp</span><span class="sxs-lookup"><span data-stu-id="b7310-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="b7310-644">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7310-644">Description</span></span>

<span data-ttu-id="b7310-645">Den här funktionen hanterar grundläggande förfrågningar som skickas av värden på kontrollens slut punkt med en USB-ljud2,0-typ.</span><span class="sxs-lookup"><span data-stu-id="b7310-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="b7310-646">Ljud 2,0 samplings frekvens (förmodad enkel fast frekvens), funktioner för volym och ljud av förfrågningar bearbetas i funktionen.</span><span class="sxs-lookup"><span data-stu-id="b7310-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="b7310-647">När begär Anden bearbetas används fördefinierade data som skickas av den senaste parametern (grupp) för att besvara begär Anden och spara kontroll ändringar.</span><span class="sxs-lookup"><span data-stu-id="b7310-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="b7310-648">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7310-648">Parameters</span></span>

- <span data-ttu-id="b7310-649">**ljud**: pekar mot ljud instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="b7310-650">**överföring**: pekar mot överförings begär ande instansen.</span><span class="sxs-lookup"><span data-stu-id="b7310-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="b7310-651">**grupp**: data grupp för process för begäran.</span><span class="sxs-lookup"><span data-stu-id="b7310-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="b7310-652">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7310-652">Return Value</span></span>

- <span data-ttu-id="b7310-653">**UX_SUCCESS** (0X00) den här åtgärden lyckades.</span><span class="sxs-lookup"><span data-stu-id="b7310-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="b7310-654">**UX_ERROR** (0Xff) fel från funktion</span><span class="sxs-lookup"><span data-stu-id="b7310-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="b7310-655">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7310-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
