---
title: Överväganden för USBX DPUMP-klass
description: USBX innehåller en DPUMP-klass för värd- och enhetssidan.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 72aa9c1e2200049bf81d64543b690edd001c4ecf9c2cdeb4c3bea5f1b03aa5b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802589"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Kapitel 3: Usbx DPUMP-klassöverväganden

USBX innehåller en DPUMP-klass för värd- och enhetssidan. Den här klassen är inte en standardklass i sig, utan snarare ett exempel som illustrerar hur du skapar en enkel enhet med hjälp av två masspipelar och skickar data fram och tillbaka på dessa två pipes. DPUMP-klassen kan användas för att starta en anpassad klass eller för äldre RS232-enheter.

FLÖDESSCHEMA FÖR USB DPUMP:

![Flödesdiagram för USB DPUMP](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>USBX DPUMP-värdklass

Värdsidan av DPUMP-klassen har två funktioner, en för att skicka data och en för att ta emot data:

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Båda funktionerna blockerar för att göra DPUMP-programmet enklare. Om det är nödvändigt att köra båda rören (IN och OUT) samtidigt måste programmet skapa en överföringstråd och en mottagningstråd.

Prototypen för skrivfunktionen ser ut så här.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Plats:

- dpump är instansen av klassen
- data_pointer pekaren till bufferten som ska skickas
- requested_length är längden på att skicka
- actual_length är den längd som skickas efter slutförandet av överföringen, antingen korrekt eller delvis.

Prototypen för den mottagande funktionen är liknande.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

Här är ett exempel på klassen värd-DPUMP där ett program skriver ett paket till enhetssidan och tar emot samma paket i mottagningen:

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

## <a name="usbx-dpump-device-class"></a>USBX DPUMP-enhetsklass

Enhetens DPUMP-klass använder en tråd som startas vid anslutning till USB-värden. Tråden väntar på att ett paket ska komma på massutfyllnadsslutpunkten. När ett paket tas emot kopieras innehållet till bufferten Bulk In endpoint (Mass in slutpunkt) och en transaktion skickas på den här slutpunkten i väntan på att värden ska utfärda en begäran om att läsa från den här slutpunkten. Detta ger en loopback-mekanism mellan slutpunkterna Bulk Out och Bulk In.
