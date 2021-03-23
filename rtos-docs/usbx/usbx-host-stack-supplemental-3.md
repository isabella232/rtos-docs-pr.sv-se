---
title: Överväganden för USBX DPUMP-klass
description: USBX innehåller en DPUMP-klass för värden och enhets sidan.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828074"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="142da-103">Kapitel 3: USBX DPUMP-klass överväganden</span><span class="sxs-lookup"><span data-stu-id="142da-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="142da-104">USBX innehåller en DPUMP-klass för värden och enhets sidan.</span><span class="sxs-lookup"><span data-stu-id="142da-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="142da-105">Den här klassen är inte en standard klass i sig själv, utan i stället ett exempel som illustrerar hur du skapar en enkel enhet med två Mass ledningar och hur du skickar data till och från dessa två ledningar.</span><span class="sxs-lookup"><span data-stu-id="142da-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="142da-106">DPUMP-klassen kan användas för att starta en anpassad klass eller för äldre RS232-enheter.</span><span class="sxs-lookup"><span data-stu-id="142da-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="142da-107">Flödes diagram för USB-DPUMP:</span><span class="sxs-lookup"><span data-stu-id="142da-107">USB DPUMP flow chart:</span></span>

![Flödes diagram för USB-DPUMP](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="142da-109">Värd klass för USBX-DPUMP</span><span class="sxs-lookup"><span data-stu-id="142da-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="142da-110">Värd sidan i DPUMP-klassen har två funktioner, en för att skicka data och en för att ta emot data:</span><span class="sxs-lookup"><span data-stu-id="142da-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="142da-111">Båda funktionerna blockeras för att göra DPUMP-programmet lättare.</span><span class="sxs-lookup"><span data-stu-id="142da-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="142da-112">Om båda pipes (IN och ut) måste köras samtidigt måste programmet skapa en överförings tråd och en Receive-tråd.</span><span class="sxs-lookup"><span data-stu-id="142da-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="142da-113">Prototypen för funktionen Skriv är följande.</span><span class="sxs-lookup"><span data-stu-id="142da-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="142da-114">Plats:</span><span class="sxs-lookup"><span data-stu-id="142da-114">Where:</span></span>

- <span data-ttu-id="142da-115">dpump är instansen av klassen</span><span class="sxs-lookup"><span data-stu-id="142da-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="142da-116">data_pointer är pekaren till den buffert som ska skickas</span><span class="sxs-lookup"><span data-stu-id="142da-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="142da-117">requested_length är den längd som ska skickas</span><span class="sxs-lookup"><span data-stu-id="142da-117">requested_length is the length to send</span></span>
- <span data-ttu-id="142da-118">actual_length är den längd som skickas när överföringen har slutförts, antingen korrekt eller delvis.</span><span class="sxs-lookup"><span data-stu-id="142da-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="142da-119">Prototypen för funktionen Inleverera är liknande.</span><span class="sxs-lookup"><span data-stu-id="142da-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="142da-120">Här är ett exempel på en värd DPUMP-klass där ett program skriver ett paket till enhets sidan och tar emot samma paket för mottagningen:</span><span class="sxs-lookup"><span data-stu-id="142da-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="142da-121">USBX DPUMP-enhets klass</span><span class="sxs-lookup"><span data-stu-id="142da-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="142da-122">Enhetens DPUMP-klass använder en tråd som startas vid anslutning till USB-värden.</span><span class="sxs-lookup"><span data-stu-id="142da-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="142da-123">Tråden väntar på ett paket som kommer från den utgående slut punkten.</span><span class="sxs-lookup"><span data-stu-id="142da-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="142da-124">När ett paket tas emot kopierar det innehållet till Mass-och slut punktens buffert och publicerar en transaktion på den här slut punkten, väntar på att värden ska utfärda en begäran om att läsa från den här slut punkten.</span><span class="sxs-lookup"><span data-stu-id="142da-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="142da-125">Detta ger en loopback-mekanism mellan utsamlings-och Mass slut punkter.</span><span class="sxs-lookup"><span data-stu-id="142da-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
