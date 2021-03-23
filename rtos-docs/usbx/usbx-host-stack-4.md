---
title: Kapitel 4 – Beskrivning av USBX-värd tjänster
description: Läs mer om USBX-värd tjänsterna.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828455"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Kapitel 4 – Beskrivning av USBX-värd tjänster

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Initiera USBX för värd åtgärd.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Beskrivning

Den här funktionen initierar USB-värdstyrenheten. Det tillhandahållna minnes området kommer att konfigureras för intern användning av USBX. Om UX_SUCCESS returneras är USBX redo för värd styrenhet och klass registrering.

### <a name="input-parameter"></a>Indataparameter

- **system_change_function** Pekare till valfri callback-rutin för att meddela program om enhets ändringar.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) lyckades.
- **UX_MEMORY_INSUFFICIENT** (0X12) en minnesallokering misslyckades.

### <a name="example"></a>Exempel

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Avbryt alla transaktioner som är kopplade till en överföringsbegäran för en slut punkt.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Beskrivning

Den här funktionen avbryter alla transaktioner som är aktiva eller väntar på en angiven överföringsbegäran som är kopplad till en slut punkt. Den överförings förfrågan har en kopplad motringning, anropas funktionen motringning med UX_TRANSACTION_ABORTEDs status.

### <a name="input-parameter"></a>Indataparameter

- **slut punkt** Pekare till en slut punkt.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) inga fel.
- Slut punkts referensen för **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) är ogiltig.

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

Hämta pekaren till en klass behållare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar en pekare till klass containern. En klass behöver hämta sin behållare från USB-stacken för att söka efter instanser när en klass eller ett program vill öppna en enhet.

> [!NOTE]
> C-strängen för class_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Parametrar

- **class_name** Pekar mot klass namnet.
- **klass** En pekare som uppdaterats av funktions anropet och som innehåller klass behållaren för namnet på klassen.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) inga fel, i returnera klass fältet arkiveras med pekaren till klass behållaren.
- **UX_HOST_CLASS_UNKNOWN** (0x59)-klassen är okänd i stacken.

### <a name="example"></a>Exempel

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

Registrera en USB-klass på USB-stacken.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Beskrivning

Den här funktionen registrerar en USB-klass i USB-stacken. Klassen måste ange en start punkt för USB-stacken för att skicka kommandon som följande.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> C-strängen för *class_name* måste vara null-terminerad och längden på den (utan själva null-begränsaren) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **class_name** Pekar till namnet på klassen. giltiga poster finns i filen ux_system_initialize. c under USB-klasserna för USBX.
- **class_entry_address** Adress till post-funktionen för klassen.

### <a name="return-values"></a>Retur värden

- Klassen **UX_SUCCESS** (0x00) har installerats.
- **UX_MEMORY_ARRAY_FULL** (0x1a) Det går inte att lagra den här klassen med mer minne.
- Värd klassen för **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) är redan installerad.

### <a name="example"></a>Exempel:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

Skapa en ny klass instans för en klass behållare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Beskrivning

Den här funktionen skapar en ny klass instans för en klass behållare. Instansen för en klass ingår inte i klass koden för att minska klass komplexiteten. I stället är varje klass instans kopplad till klass behållaren som finns i huvud stacken.

### <a name="parameters"></a>Parametrar

- **klass** Pekare till klass behållaren.
- **class_instance** Pekare till klass instansen som ska skapas.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) klass instansen anslöts till klass containern.

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

Förstör en klass instans för en klass behållare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Beskrivning

Den här funktionen förstör en klass instans för en klass behållare.

### <a name="parameters"></a>Parametrar

- **klass** Pekare till klass behållaren.
- **class_instance** Pekar på den instans som ska förstöras.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) klass instansen har förstörts.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) klass instansen är inte kopplad till klass containern.

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

Hämta en klass instans pekare för en speciell klass.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar en klass instans pekare för en speciell klass. Instansen för en klass ingår inte i klass koden för att minska klass komplexiteten. Varje klass instans är i stället kopplad till klass behållaren. Den här funktionen används för att söka efter klass instanser i en klass behållare.

### <a name="parameters"></a>Parametrar

- **klass** Pekare till klass behållaren.
- **class_index** Ett index som ska användas av funktions anropet i listan över anslutna klasser till behållaren.
- **class_instance** Pekare till den instans som ska returneras av funktions anropet.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) klass instansen påträffades.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b) det finns inga fler klass instanser kopplade till klass behållaren.

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

Hämta en pekare till en konfigurations behållare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar en konfigurations behållare baserat på en enhets referens och ett konfigurations index.

### <a name="parameters"></a>Parametrar

- **enhet** Pekar till enhets behållaren som äger den begärda konfigurationen.
- **configuration_index** Index för den konfiguration som ska genomsökas.
- **konfiguration** Adress till den-pekare till den konfigurations behållare som ska returneras.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) konfigurationen hittades.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) enhets containern finns inte.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) konfigurations referensen för indexet finns inte.

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

Välj en speciell konfiguration för en enhet.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Beskrivning

Den här funktionen väljer en speciell konfiguration för en enhet. När den här konfigurationen är inställd på enheten aktive ras som standard alla enhets gränssnitt och den tillhör ande alternativa inställningen 0 på enheten. Om enhets-och gränssnitts klassen vill ändra inställningen för ett visst gränssnitt måste den utfärda ett **ux_host_stack_interface_setting_select** tjänst anrop.

### <a name="parameters"></a>Parametrar

- **konfiguration** Pekar till den konfigurations behållare som ska aktive ras för den här enheten.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) konfigurations valet har slutförts.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) konfigurations referensen finns inte.
- **UX_OVER_CURRENT_CONDITION** (0X43) ett över aktuellt villkor finns på bussen för den här konfigurationen.

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

Hämta en pekare till en enhets behållare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar en enhets behållare baserat på dess index. Enhets indexet börjar med 0. Observera att indexet är en ULONG eftersom vi kan ha flera styrenheter och ett byte-index kanske inte räcker till. Enhets indexet ska inte förväxlas med den enhets adress som är buss-/regionsspecifika.

### <a name="parameters"></a>Parametrar

- **device_index** Enhetens index.
- **enhet** Adress till den enhets behållare som ska returneras.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) enhets containern finns och returneras
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) Okänd enhet

### <a name="example"></a>Exempel

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Hämta en slut punkts behållare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar en slut punkts behållare baserat på gränssnitts referensen och ett slut punkts index. Det förutsätts att den alternativa inställningen för gränssnittet har marker ATS eller att standardinställningen används innan de slut punkter som genomsöks.

### <a name="parameters"></a>Parametrar

- **gränssnitt** Pekare till den gränssnitts behållare som innehåller den begärda slut punkten.
- **endpoint_index** Index för slut punkten i det här gränssnittet.
- **slut punkt** Adress till den slut punkts behållare som ska returneras.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) slut punkts containern finns och returneras.
- Det angivna **UX_INTERFACE_HANDLE_UNKNOWN** -gränssnittet (0x52) finns inte.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0X53) slut punkts indexet finns inte.

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

Registrera en USB-styrenhet i USB-stacken.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Beskrivning

Den här funktionen registrerar en USB-styrenhet till USB-stacken. Det allokerar främst det minne som används av den här styrenheten och skickar initierings kommandot till kontrollanten.

### <a name="parameters"></a>Parametrar

- **hcd_name** Namn på värd styrenheten
- **hcd_function** Funktionen i värd styrenheten som ansvarar för initieringen.
- **hcd_param1** Den IO-eller minnes resurs som används av HCD.
- **hcd_param2** IRQ som används av värd styrenheten.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) kontrollanten initierades korrekt.
- **UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för den här styrenheten.
- **UX_PORT_RESET_FAILED** (0X31) Det gick inte att återställa kontrollanten.
- **UX_CONTROLLER_INIT_FAILED** (0x32) styrenheten kunde inte initieras korrekt.

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

Hämta en gränssnitts container pekare.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar en gränssnitts behållare baserat på en konfigurations referens, ett gränssnitts index och ett alternativ inställnings index.

### <a name="parameters"></a>Parametrar

- **konfiguration** Pekare till den konfigurations behållare som äger gränssnittet.
- **interface_index** Gränssnitts index som ska genomsökas.
- **alternate_setting_index** Alternativ i det gränssnitt som ska genomsökas.
- **gränssnitt** Adress till den gränssnitts container pekare som ska returneras.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) gränssnitts behållaren för gränssnitts indexet och den alternativa inställningen hittades och returnerades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) konfigurationen finns inte.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) gränssnittet finns inte.

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

### <a name="description"></a>Beskrivning

Den här funktionen väljer en specifik alternativ inställning för ett angivet gränssnitt som tillhör den valda konfigurationen. Den här funktionen används för att ändra från standard alternativ inställningen till en ny inställning eller att gå tillbaka till standard alternativ inställningen. När en ny alternativ inställning väljs, är tidigare slut punkts egenskaper ogiltiga och bör läsas in igen.

### <a name="input-parameter"></a>Indataparameter

- **gränssnitt** Pekar till gränssnitts behållaren vars alternativa inställning ska väljas.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) den alternativa inställningen för det här gränssnittet har marker ATS.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) gränssnittet finns inte.

### <a name="example"></a>Exempel

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Avbryt en väntande överförings förfrågan.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Beskrivning

Den här funktionen avbryter en väntande överförings förfrågan som redan har skickats. Den här funktionen avbryter bara en begäran om överföring. Anropet till funktionen kommer att ha statusen UX_TRANSFER REQUEST_STATUS_ABORT.

### <a name="parameters"></a>Parametrar

- **överförings förfrågan** Pekare till överförings förfrågan som ska avbrytas.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) USB-överföringen för den här överföringsbegäran har avbrutits.

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

### <a name="description"></a>Beskrivning

Den här funktionen utför en USB-transaktion. Vid inmatning ger överföringsbegäran den valda slut punkts pipe för den här transaktionen och de parametrar som är kopplade till överföringen (data nytto Last, transaktions längd). För Control pipe blockeras transaktionen och kommer bara att returneras när de tre faserna av kontroll överföringen har slutförts eller om det finns ett tidigare fel. För andra pipes kommer USB-stacken att schemalägga transaktionen på USB-enheten, men väntar inte på slut för ande. Varje överföringsbegäran för icke-blockerande pipes måste ange en rutin hanterare för slut för ande.

När funktions anropet returnerar, bör statusen för överförings förfrågan undersökas eftersom den innehåller resultatet av transaktionen.

### <a name="input-parameter"></a>Indataparameter

- **transfer_request** Pekare till överförings förfrågan. Överföringsbegäran innehåller all nödvändig information som krävs för överföringen.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) USB-överföringen av denna överföringsbegäran schemalades korrekt. Status koden för överföringsbegäran bör undersökas när överföringsbegäran slutförs.
- **UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för att allokera nödvändiga styrenhets resurser.
- **UX_TRANSFER_NOT_READY** (0x25) enheten var i ett ogiltigt tillstånd – måste vara ansluten, adresserad eller konfigurerad.

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
