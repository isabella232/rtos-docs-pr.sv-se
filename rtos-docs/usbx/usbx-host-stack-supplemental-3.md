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
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Kapitel 3: USBX DPUMP-klass överväganden

USBX innehåller en DPUMP-klass för värden och enhets sidan. Den här klassen är inte en standard klass i sig själv, utan i stället ett exempel som illustrerar hur du skapar en enkel enhet med två Mass ledningar och hur du skickar data till och från dessa två ledningar. DPUMP-klassen kan användas för att starta en anpassad klass eller för äldre RS232-enheter.

Flödes diagram för USB-DPUMP:

![Flödes diagram för USB-DPUMP](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>Värd klass för USBX-DPUMP

Värd sidan i DPUMP-klassen har två funktioner, en för att skicka data och en för att ta emot data:

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Båda funktionerna blockeras för att göra DPUMP-programmet lättare. Om båda pipes (IN och ut) måste köras samtidigt måste programmet skapa en överförings tråd och en Receive-tråd.

Prototypen för funktionen Skriv är följande.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Plats:

- dpump är instansen av klassen
- data_pointer är pekaren till den buffert som ska skickas
- requested_length är den längd som ska skickas
- actual_length är den längd som skickas när överföringen har slutförts, antingen korrekt eller delvis.

Prototypen för funktionen Inleverera är liknande.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

Här är ett exempel på en värd DPUMP-klass där ett program skriver ett paket till enhets sidan och tar emot samma paket för mottagningen:

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

## <a name="usbx-dpump-device-class"></a>USBX DPUMP-enhets klass

Enhetens DPUMP-klass använder en tråd som startas vid anslutning till USB-värden. Tråden väntar på ett paket som kommer från den utgående slut punkten. När ett paket tas emot kopierar det innehållet till Mass-och slut punktens buffert och publicerar en transaktion på den här slut punkten, väntar på att värden ska utfärda en begäran om att läsa från den här slut punkten. Detta ger en loopback-mekanism mellan utsamlings-och Mass slut punkter.
