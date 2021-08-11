---
title: Kapitel 4 – Beskrivning av USBX-värdtjänster
description: Läs mer om USBX-värdtjänsterna.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6cbeff83d8e3812f13aa3f8f66d4013b70490d556911939186b4b43840aac50d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790691"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Kapitel 4 – Beskrivning av USBX-värdtjänster

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Initiera USBX för värdåtgärd.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Description

Den här funktionen initierar USB-värdstacken. Det angivna minnesområdet kommer att konfigureras för intern USBX-användning. Om UX_SUCCESS returneras är USBX redo för värdstyrenhet och klassregistrering.

### <a name="input-parameter"></a>Indataparameter

- **system_change_function** Pekare till valfri motringningsrutin för att meddela tillämpning av enhetsändringar.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Lyckad initiering.
- **UX_MEMORY_INSUFFICIENT** (0x12) En minnesallokering misslyckades.

### <a name="example"></a>Exempel

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Avbryt alla transaktioner som är kopplade till en överföringsbegäran för en slutpunkt.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Description

Den här funktionen avbryter alla aktiva eller väntande transaktioner för en specifik överföringsbegäran som är kopplad till en slutpunkt. Om överföringsbegäran har en återanropsfunktion kopplad anropas återanropsfunktionen med UX_TRANSACTION_ABORTED status.

### <a name="input-parameter"></a>Indataparameter

- **slutpunkt** Pekare till en slutpunkt.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Inga fel.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Slutpunktshandtaget är inte giltigt.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

Hämta pekaren till en klasscontainer.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Description

Den här funktionen returnerar en pekare till klasscontainern. En klass måste hämta sin container från USB-stacken för att söka efter instanser när en klass eller ett program vill öppna en enhet.

> [!NOTE]
> C-strängen för class_name måste vara NULL-avslutad och längden på den (utan själva NULL-terminatorn) får inte vara större än UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Parametrar

- **class_name** Pekare till klassnamnet.
- **klass** En pekare som uppdateras av funktionsanropet som innehåller klasscontainern för namnet på klassen.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Inga fel, när klassfältet returneras arkiveras med pekaren till klasscontainern.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Klass är okänd av stacken.

### <a name="example"></a>Exempel

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

Registrera en USB-klass till USB-stacken.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Description

Den här funktionen registrerar en USB-klass till USB-stacken. Klassen måste ange en startpunkt för USB-stacken för att skicka kommandon som följande.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> C-strängen *för class_name* måste vara NULL-avslutad och längden på den (utan själva NULL-terminatorn) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **class_name** Om du pekar på namnet på klassen finns giltiga poster i filen ux_system_initialize.c under USB-klasserna för USBX.
- **class_entry_address** Adressen till entry-funktionen för klassen .

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Har installerats.
- **UX_MEMORY_ARRAY_FULL** (0x1a) Inget mer minne för att lagra den här klassen.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Värdklass redan installerad.

### <a name="example"></a>Exempel:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

Skapa en ny klassinstans för en klasscontainer.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Description

Den här funktionen skapar en ny klassinstans för en klasscontainer. Instansen av en klass ingår inte i klasskoden för att minska klasskomplexiteten. I stället är varje klassinstans kopplad till klasscontainern som finns i huvudstacken.

### <a name="parameters"></a>Parametrar

- **klass** Pekare till klasscontainern.
- **class_instance** Pekare till klassinstansen som ska skapas.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Klassinstansen kopplades till klasscontainern.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

Förstöra en klassinstans för en klasscontainer.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Description

Den här funktionen förstör en klassinstans för en klasscontainer.

### <a name="parameters"></a>Parametrar

- **klass** Pekare till klasscontainern.
- **class_instance** Pekare till instansen som ska förstöras.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Klassinstansen förstörs.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Klassinstansen är inte kopplad till klasscontainern.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

Hämta en klassinstans pekare för en specifik klass.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Description

Den här funktionen returnerar en klassinstans pekare för en specifik klass. Instansen av en klass ingår inte i klasskoden för att minska klasskomplexiteten. I stället är varje klassinstans kopplad till klasscontainern. Den här funktionen används för att söka efter klassinstanser i en klasscontainer.

### <a name="parameters"></a>Parametrar

- **klass** Pekare till klasscontainern.
- **class_index** Ett index som ska användas av funktionsanropet i listan över anslutna klasser till containern.
- **class_instance** Pekare till den instans som ska returneras av funktionsanropet.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Klassinstansen hittades.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Det finns inga fler klassinstanser kopplade till klasscontainern.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

Hämta en pekare till en konfigurationscontainer.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Description

Den här funktionen returnerar en konfigurationscontainer baserat på en enhetshanterare och ett konfigurationsindex.

### <a name="parameters"></a>Parametrar

- **enhet** Pekare till den enhetscontainer som äger den begärda konfigurationen.
- **configuration_index** Index för konfigurationen som ska genomsökas.
- **konfiguration** Adressen för pekaren till konfigurationscontainern som ska returneras.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Konfigurationen hittades.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) Enhetscontainern finns inte.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Indexets konfigurationshanterare finns inte.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

Välj en specifik konfiguration för en enhet.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Description

Den här funktionen väljer en specifik konfiguration för en enhet. När den här konfigurationen är inställd på enheten aktiveras som standard varje enhetsgränssnitt och dess associerade alternativa inställning 0 på enheten. Om enhets-/gränssnittsklassen vill ändra inställningen för ett visst gränssnitt måste den utfärda ett ux_host_stack_interface_setting_select service-anrop. 

### <a name="parameters"></a>Parametrar

- **konfiguration** Pekare till den konfigurationscontainer som ska aktiveras för den här enheten.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Valet av konfiguration lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Konfigurationshandtaget finns inte.
- **UX_OVER_CURRENT_CONDITION** (0x43) Ett över aktuellt villkor finns på buss för den här konfigurationen.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

Hämta en pekare till en enhetscontainer.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Description

Den här funktionen returnerar en enhetscontainer baserat på dess index. Enhetsindexet börjar med 0. Observera att indexet är en ULONG eftersom vi kan ha flera styrenheter och ett byteindex kanske inte räcker. Enhetsindexet ska inte förväxlas med den enhetsadress som är bussspecifik.

### <a name="parameters"></a>Parametrar

- **device_index** Index för enheten.
- **enhet** Adressen till pekaren som enhetscontainern ska returnera.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Enhetscontainern finns och returneras
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) Okänd enhet

### <a name="example"></a>Exempel

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Hämta en slutpunktscontainer.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Description

Den här funktionen returnerar en slutpunktscontainer baserat på gränssnittshandtaget och ett slutpunktsindex. Det förutsätts att den alternativa inställningen för gränssnittet har valts eller att standardinställningen används innan slutpunkterna genomsöks.

### <a name="parameters"></a>Parametrar

- **gränssnitt** Pekare till gränssnittscontainern som innehåller den begärda slutpunkten.
- **endpoint_index** Index för slutpunkten i det här gränssnittet.
- **slutpunkt** Adressen till den slutpunktscontainer som ska returneras.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Slutpunktscontainern finns och returneras.
- **det UX_INTERFACE_HANDLE_UNKNOWN** (0x52)-gränssnittet finns inte.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Slutpunktsindex finns inte.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

Registrera en USB-styrenhet till USB-stacken.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Description

Den här funktionen registrerar en USB-styrenhet till USB-stacken. Den allokerar främst det minne som används av den här styrenheten och skickar initieringskommandot till kontrollanten.

### <a name="parameters"></a>Parametrar

- **hcd_name** Värdstyrenhetens namn
- **hcd_function** Funktionen i värdstyrenheten som ansvarar för initieringen.
- **hcd_param1** I/H eller minnesresursen som används av hcd.
- **hcd_param2** Den IRQ som används av värdstyrenheten.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Kontrollanten initierades korrekt.
- **UX_MEMORY_INSUFFICIENT** (0x12) Det finns inte tillräckligt med minne för den här styrenheten.
- **UX_PORT_RESET_FAILED** (0x31) Återställningen av kontrollanten misslyckades.
- **UX_CONTROLLER_INIT_FAILED** (0x32) Kontrollanten kunde inte initieras korrekt.

### <a name="example"></a>Exempel

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

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

Hämta en gränssnittscontainer pekare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Description

Den här funktionen returnerar en gränssnittscontainer baserat på en konfigurationshanterare, ett gränssnittsindex och ett alternativt inställningsindex.

### <a name="parameters"></a>Parametrar

- **konfiguration** Pekare till konfigurationscontainern som äger gränssnittet.
- **interface_index** Gränssnittsindex som ska genomsökas.
- **alternate_setting_index** Alternativ inställning i gränssnittet för att söka.
- **gränssnitt** Adressen till gränssnittscontainern som ska returneras.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Gränssnittscontainern för gränssnittsindexet och den alternativa inställningen hittades och returnerades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Konfigurationen finns inte.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Gränssnittet finns inte.

### <a name="example"></a>Exempel

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

Välj en alternativ inställning för ett gränssnitt.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Description

Den här funktionen väljer en specifik alternativ inställning för ett visst gränssnitt som hör till den valda konfigurationen. Den här funktionen används för att ändra från den alternativa standardinställningen till en ny inställning eller för att gå tillbaka till den alternativa standardinställningen. När en ny alternativ inställning väljs är de tidigare slutpunktsegenskaperna ogiltiga och bör läsas in på nytt.

### <a name="input-parameter"></a>Indataparameter

- **gränssnitt** Pekare till gränssnittscontainern vars alternativa inställning ska väljas.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Den alternativa inställningen för det här gränssnittet har valts.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Gränssnittet finns inte.

### <a name="example"></a>Exempel

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Avbryt en väntande överföringsbegäran.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Description

Den här funktionen avbryter en väntande överföringsbegäran som har skickats tidigare. Den här funktionen avbryter bara en specifik överföringsbegäran. Anropet tillbaka till funktionen har UX_TRANSFER REQUEST_STATUS_ABORT status.

### <a name="parameters"></a>Parametrar

- **överföringsbegäran** Pekare till överföringsbegäran som ska avbrytas.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) USB-överföringen för den här överföringsbegäran avbröts.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

Begär en USB-överföring.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Description

Den här funktionen utför en USB-transaktion. Vid inmatningen ger överföringsbegäran den slutpunktspipe som valts för den här transaktionen och de parametrar som är associerade med överföringen (datanyttolast, transaktionslängd). För Kontrollpipe- blockeras transaktionen och returneras endast när de tre faserna av kontrollöverföringen har slutförts eller om det finns ett tidigare fel. För andra pipes schemalägger USB-stacken transaktionen via USB men väntar inte på att den ska slutföras. Varje överföringsbegäran för icke-blockerande pipes måste ange en slutföranderutinhanterare.

När funktionsanropet returnerar bör status för överföringsbegäran undersökas eftersom den innehåller resultatet av transaktionen.

### <a name="input-parameter"></a>Indataparameter

- **transfer_request** Pekare till överföringsbegäran. Överföringsbegäran innehåller all nödvändig information som krävs för överföringen.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) USB-överföringen för den här överföringsbegäran har schemalagts korrekt. Statuskoden för överföringsbegäran bör undersökas när överföringsbegäran har slutförts.
- **UX_MEMORY_INSUFFICIENT** (0x12) Det finns inte tillräckligt med minne för att allokera nödvändiga kontrollantresurser.
- **UX_TRANSFER_NOT_READY** (0x25) Enheten var i ett ogiltigt tillstånd – måste vara ANSLUTEN, ADRESSERad eller KONFIGURERAD.

### <a name="example"></a>Exempel:

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
