---
title: Kapitel 3 – funktionella komponenter i USBX Device stack
description: Det här kapitlet innehåller en beskrivning av stacken med USBX inbäddade USB-enheter med hög prestanda från ett funktionellt perspektiv.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a20fed71cbee8c50519be4a971eb191e0cc93915
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827426"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="5ec1b-103">Kapitel 3 – funktionella komponenter i USBX Device stack</span><span class="sxs-lookup"><span data-stu-id="5ec1b-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="5ec1b-104">Det här kapitlet innehåller en beskrivning av stacken med USBX inbäddade USB-enheter med hög prestanda från ett funktionellt perspektiv.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="5ec1b-105">Översikt över körning</span><span class="sxs-lookup"><span data-stu-id="5ec1b-105">Execution Overview</span></span>

<span data-ttu-id="5ec1b-106">USBX för enheten består av flera komponenter.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="5ec1b-107">Initiering</span><span class="sxs-lookup"><span data-stu-id="5ec1b-107">Initialization</span></span>
- <span data-ttu-id="5ec1b-108">Program gränssnitts anrop</span><span class="sxs-lookup"><span data-stu-id="5ec1b-108">Application interface calls</span></span>
- <span data-ttu-id="5ec1b-109">Enhets klasser</span><span class="sxs-lookup"><span data-stu-id="5ec1b-109">Device Classes</span></span>
- <span data-ttu-id="5ec1b-110">USB-enhets stack</span><span class="sxs-lookup"><span data-stu-id="5ec1b-110">USB Device Stack</span></span>
- <span data-ttu-id="5ec1b-111">Enhets styrenhet</span><span class="sxs-lookup"><span data-stu-id="5ec1b-111">Device controller</span></span>
- <span data-ttu-id="5ec1b-112">VBUS Manager</span><span class="sxs-lookup"><span data-stu-id="5ec1b-112">VBUS manager</span></span>

<span data-ttu-id="5ec1b-113">Följande diagram illustrerar USBX Device-stacken.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-113">The following diagram illustrates the USBX Device stack.</span></span>

![USBX Device-stack](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="5ec1b-115">Initiering</span><span class="sxs-lookup"><span data-stu-id="5ec1b-115">Initialization</span></span>

<span data-ttu-id="5ec1b-116">Funktionen ***ux_system_initialize*** måste anropas för att aktivera USBX.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="5ec1b-117">Den här funktionen initierar minnes resurserna för USBX.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="5ec1b-118">Funktionen ***ux_device_stack_initialize*** måste anropas för att kunna aktivera enhets anläggningar för USBX.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="5ec1b-119">Den här funktionen kommer att initiera alla resurser som används av USBX Device stack, till exempel ThreadX-trådar, mutexer och semaforer.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="5ec1b-120">Det är upp till program initieringen att aktivera USB-styrenheten och en eller flera USB-klasser.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="5ec1b-121">Till skillnad från USB-värdstyrenheten kan enhets sidan bara ha en USB Controller-drivrutin som körs när som helst.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="5ec1b-122">När klasserna har registrerats till stacken och enhets styrenhetens (a) initierings funktion har anropats, är bussen aktiv och stacken svarar på kommandona för Bus-återställning och värd uppräkning.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="5ec1b-123">Program gränssnitts anrop</span><span class="sxs-lookup"><span data-stu-id="5ec1b-123">Application Interface Calls</span></span>

<span data-ttu-id="5ec1b-124">Det finns två nivåer av API: er i USBX.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="5ec1b-125">Stack-API: er för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="5ec1b-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="5ec1b-126">API: er för USB-enhets klass</span><span class="sxs-lookup"><span data-stu-id="5ec1b-126">USB Device Class APIs</span></span>

<span data-ttu-id="5ec1b-127">Normalt behöver ett USBX-program inte anropa någon av USB-API: erna för USB-enhet.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="5ec1b-128">De flesta program får bara åtkomst till API: er för USB-klass.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="5ec1b-129">Stack-API: er för USB-enhet</span><span class="sxs-lookup"><span data-stu-id="5ec1b-129">USB Device Stack APIs</span></span>

<span data-ttu-id="5ec1b-130">API: erna för enhets stacken ansvarar för registreringen av USBX-enhets komponenter, till exempel klasser och enhets ramverket.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="5ec1b-131">API: er för USB-enhets klass</span><span class="sxs-lookup"><span data-stu-id="5ec1b-131">USB Device Class APIs</span></span>

<span data-ttu-id="5ec1b-132">Klass-API: erna är särskilt speciella för varje USB-klass.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="5ec1b-133">De flesta vanliga API: er för USB-klasser tillhandahåller tjänster som att öppna/stänga en enhet och läsa från och skriva till en enhet.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="5ec1b-134">API: erna liknar värd sidans typ.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="5ec1b-135">Enhets ramverk</span><span class="sxs-lookup"><span data-stu-id="5ec1b-135">Device Framework</span></span>

<span data-ttu-id="5ec1b-136">USB-enhetens sida ansvarar för definitionen av enhets ramverket.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="5ec1b-137">Enhets ramverket är uppdelat i tre kategorier, enligt beskrivningen i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="5ec1b-138">Definition av komponenterna i enhets ramverket</span><span class="sxs-lookup"><span data-stu-id="5ec1b-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="5ec1b-139">Definitionen av varje komponent i enhets ramverket är relaterad till enhetens beskaffenhet och de resurser som används av enheten.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="5ec1b-140">Följande är de viktigaste kategorierna.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-140">Following are the main categories.</span></span>

- <span data-ttu-id="5ec1b-141">Enhets Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ec1b-141">Device Descriptor</span></span>
- <span data-ttu-id="5ec1b-142">Konfigurations Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ec1b-142">Configuration Descriptor</span></span>
- <span data-ttu-id="5ec1b-143">Gränssnitts Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ec1b-143">Interface Descriptor</span></span>
- <span data-ttu-id="5ec1b-144">Slut punkts Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ec1b-144">Endpoint Descriptor</span></span>

<span data-ttu-id="5ec1b-145">USBX stöder enhets komponent definition för både hög och fullständig hastighet (låg hastighet behandlas på samma sätt som full hastighet).</span><span class="sxs-lookup"><span data-stu-id="5ec1b-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="5ec1b-146">Detta gör att enheten fungerar annorlunda när den är ansluten till en hög hastighets-eller full hastighets värd.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="5ec1b-147">De typiska skillnaderna är storleken på varje slut punkt och den ström som förbrukas av enheten.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="5ec1b-148">Definitionen av enhets komponenten tar formen av en byte-sträng som följer USB-specifikationen.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="5ec1b-149">Definitionen är sammanhängande och den ordning som ramverket är representerat i minnet är samma som det som returneras till värden under uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="5ec1b-150">Följande är ett exempel på ett enhets ramverk för en USB-flash-disk med hög hastighet.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="5ec1b-151">Definition av strängarna i enhets ramverket</span><span class="sxs-lookup"><span data-stu-id="5ec1b-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="5ec1b-152">Strängar är valfria i en enhet.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-152">Strings are optional in a device.</span></span> <span data-ttu-id="5ec1b-153">Syftet med detta är att låta USB-värden veta om enhetens tillverkare, produktens namn och revisions numret genom Unicode-strängarna.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="5ec1b-154">Huvud strängarna är inbäddade index i enhets beskrivarna.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="5ec1b-155">Ytterligare sträng index kan bäddas in i enskilda gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="5ec1b-156">Förutsatt att enhets ramverket ovan har tre sträng index inbäddade i enhets beskrivningen kan sträng Ramverks definitionen se ut som den här exempel koden.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

<span data-ttu-id="5ec1b-157">Om olika strängar måste användas för varje hastighet måste olika index användas när indexen är hastigheten oberoende.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="5ec1b-158">Kodningen för strängen är UNICODE-baserad.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="5ec1b-159">Mer information om UNICODE-encoding-standarden hittar du i följande publikation:</span><span class="sxs-lookup"><span data-stu-id="5ec1b-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="5ec1b-160">*Unicode-standarden, global tecken kodning, version 1., volym 1 och 2, Unicode-konsortiet, Addison-Wesley publicerings företag, läser MA.*</span><span class="sxs-lookup"><span data-stu-id="5ec1b-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="5ec1b-161">Definition av de språk som stöds av enheten för varje sträng</span><span class="sxs-lookup"><span data-stu-id="5ec1b-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="5ec1b-162">USBX har möjlighet att stödja flera språk även om engelska är standard.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="5ec1b-163">Definitionen av varje språk för sträng beskrivningar är i form av en matris med språk definition som definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="5ec1b-164">För att stödja ytterligare språk lägger du helt enkelt till språk kodens dubbla byte-definition efter den engelska standard koden.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="5ec1b-165">Språk koden har definierats av Microsoft i dokumentet.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="5ec1b-166">*Utveckla internationell program vara för Windows 95 och Windows NT, Nadine Kano, Microsoft Press, Redmond, WA*</span><span class="sxs-lookup"><span data-stu-id="5ec1b-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="5ec1b-167">VBUS Manager</span><span class="sxs-lookup"><span data-stu-id="5ec1b-167">VBUS Manager</span></span>

<span data-ttu-id="5ec1b-168">I de flesta USB-enheter är VBUS inte en del av USB-enhetens kärna utan är i stället ansluten till en extern GPIO, som övervakar linje signalen.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="5ec1b-169">Därför måste VBUS hanteras separat från enhets styrenhetens driv rutin.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="5ec1b-170">Det är upp till programmet att tillhandahålla enhets styrenheten med adressen för VBUS i/o.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="5ec1b-171">VBUS måste initieras före initieringen av enhets styrenheten.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="5ec1b-172">Beroende på plattforms specifikationen för övervakning av VBUS, är det möjligt att låta kontrollantens driv rutin hantera VBUS-signaler när VBUS i/o har initierats eller om detta inte är möjligt måste programmet tillhandahålla koden för att hantera VBUS.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="5ec1b-173">Om programmet vill hantera VBUS själva, är det enda kravet att anropa funktionen ***ux_device_stack_disconnect*** när den upptäcker att en enhet har extraherats.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="5ec1b-174">Det är inte nödvändigt att meddela kontrollanten när en enhet sätts in, eftersom styrenheten kommer att aktive ras när bussen Återställ kontrollerad/avkontrollerande signalen identifieras.</span><span class="sxs-lookup"><span data-stu-id="5ec1b-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
