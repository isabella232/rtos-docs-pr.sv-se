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
# <a name="chapter-2-usbx-host-classes-api"></a>Kapitel 2: API för USBX-värd klasser

I det här kapitlet beskrivs alla exponerade API: er för USBX-värd klasser. Följande API: er för varje klass beskrivs i detalj.

- Skrivar klass
- Ljud klass
- Asix-klass
- Pima/PTP-klass
- Prolific-klass
- Generisk serie klass

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Läsa från skrivar gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen läser från skrivar gränssnittet. Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar. En läsning tillåts bara på dubbelriktade skrivare.

### <a name="parameters"></a>Parametrar

- **skrivare**: pekar på skrivarens klass instans.
- **data_pointer**: pekar mot buffertstorleken för data nytto lasten.
- **requested_length**: längden som ska tas emot.
- **actual_length**: den längd som faktiskt mottagits.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funktionen stöds inte eftersom skrivaren inte är dubbelriktad.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, Läsning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Skriv till skrivar gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen skriver till skrivar gränssnittet. Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **skrivare**: pekar på skrivarens klass instans.
- **data_pointer**: pekar mot buffertstorleken för data nytto lasten.
- **requested_length**: längden som ska skickas.
- **actual_length**: den längd som faktiskt har skickats.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, skrivning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Utför en mjuk återställning till skrivaren.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Beskrivning

Den här funktionen utför en mjuk återställning till skrivaren.

### <a name="input-parameter"></a>Indataparameter

- **skrivare**: pekar på skrivarens klass instans.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) återställningen slutfördes.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, återställning är inte slutförd.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Hämta skrivar status

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar skrivarens status. Skrivarens status liknar LPT-statusen (1284 standard).

### <a name="parameters"></a>Parametrar

- **skrivare**: pekar på skrivarens klass instans.
- **printer_status**: adress till den status som ska returneras.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00): återställningen slutfördes.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att utföra åtgärden.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, återställning är inte slutförd

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

Hämta skrivarens enhets-ID.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar skrivarens ID-sträng för IEEE 1284 (inklusive längden i de två första byten i big endian-format).

### <a name="parameters"></a>Parametrar

- **skrivare**: pekar på skrivarens klass instans.
- **descriptor_buffer**: pekar mot en buffert för att fylla IEEE 1284-enhets-ID-sträng (inklusive längden i de första två byte som ska formateras) 
- **length**: buffertens längd i byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00): åtgärden lyckades.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att utföra åtgärden.
- **UX_TRANSFER_TIMEOUT**: 0X5c-överförings-timeout, begäran slutfördes inte
- **UX_TRANSFER_NOT_READY**: (0x25) enheten var i ett ogiltigt tillstånd – måste vara ansluten, adresserad eller konfigurerad.
- **UX_TRANSFER_STALL**: (0X21) överföring har stoppats.
- **TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.
- **TX_SEMAPHORE_ERROR** (0X0C) ogiltig inventering av semafors pekare.
- **TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Läsa från ljud gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Beskrivning

Den här funktionen läser från ljud gränssnittet. Anropet är inte blockerande. Programmet måste se till att rätt alternativ inställning har valts för ljud strömnings gränssnittet.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot klass instansen.
- **audio_transfer_request**: pekar mot ljud överförings strukturen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts
- **UX_FUNCTION_NOT_SUPPORTED**"(0x54)-funktionen stöds inte

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

Skriv till ljud gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Beskrivning

Den här funktionen skriver till ljud gränssnittet. Anropet är inte blockerande. Programmet måste se till att rätt alternativ inställning har valts för ljud strömnings gränssnittet.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot klassen Audio-klass
- **audio_transfer_request**: pekar mot ljud överförings strukturen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) gränssnitt är felaktigt.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

Hämta en speciell kontroll från ljud kontroll gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Beskrivning

Den här funktionen läser en speciell kontroll från ljud kontroll gränssnittet.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot klassen Audio-klass
- **audio_control**: pekar mot ljud kontroll strukturen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

Ange en speciell kontroll för ljud kontroll gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

* * Beskrivning * *

Den här funktionen anger en speciell kontroll för ljud kontroll gränssnittet.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot klassen Audio-klass
- **audio_control**: pekar mot ljud kontroll strukturen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

Ange ett alternativt inställnings gränssnitt för ljud strömnings gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Beskrivning

Den här funktionen ställer in rätt alternativ gränssnitt för ljud strömnings gränssnittet enligt en speciell samplings struktur.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot klass instansen.
- **audio_sampling**: pekar mot ljud samplings strukturen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt
- **UX_NO_ALTERNATE_SETTING**: (0X5e) ingen alternativ inställning för samplings värden

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

Hämta möjliga samplings inställningar för ljud strömnings gränssnitt.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar, en i taget, alla möjliga samplings inställningar som är tillgängliga i de olika alternativen för ljud strömnings gränssnittet. Första gången funktionen används måste alla fält i den anropande struktur pekaren återställas. Funktionen returnerar en speciell uppsättning strömmande värden vid RETUR om inte slutet på de alternativa inställningarna har uppnåtts. När den här funktionen återanvänds, kommer de tidigare samplings värdena att användas för att hitta nästa samplings värde.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot klass instansen.
- **audio_sampling**: pekar mot ljud samplings strukturen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54)-funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) felaktigt gränssnitt
- **UX_NO_ALTERNATE_SETTING**: (0X5e) ingen alternativ inställning för samplings värden

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Läsa från asix-gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen läser från asix-gränssnittet. Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **asix**: pekar mot instans av asix-klassen.
- **data_pointer**: pekar mot buffertstorleken för data nytto lasten.
- **requested_length**: längden som ska tas emot.
- **actual_length**: den längd som faktiskt mottagits.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, Läsning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Skriv till asix-gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Beskrivning

Den här funktionen skriver till asix-gränssnittet. Anropet är inte blockerat.

### <a name="parameters"></a>Parametrar

- **asix**: pekar mot instans av asix-klassen.
- **paket**: netx-datapaket

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_ERROR**: (0xFF) Det gick inte att begära överföring.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Öppna en session mellan initierare och svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Beskrivning

Den här funktionen öppnar en session mellan en PIMA-initierare och en PIMA-svarare. När en session har öppnats kan de flesta PIMA-kommandon köras.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_sessio**: pekare till pima session<

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0X00) session har öppnats
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E)-sessionen är redan öppen

### <a name="example"></a>Exempel

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Stäng en session mellan initierare och svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Beskrivning

Den här funktionen stänger en session som tidigare har öppnats mellan en PIMA-initierare och en PIMA-svarare. När en session har stängts går det inte längre att köra de flesta PIMA-kommandon.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-sessionen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) sessionen stängdes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.

### <a name="example"></a>Exempel

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Hämta lagrings-ID-matrisen från svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar lagrings-ID-matrisen från svararen.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **storage_ids_array**: matris där lagrings-ID: n ska returneras
- **storage_id_length**: lagrings mat ris längden

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) matrisen med LAGRINGS-ID har fyllts i
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

Hämta lagrings informationen från svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar lagrings informationen för en lagrings behållare med värde *storage_id*.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **storage_id**: ID för lagrings containern
- **lagring**: pekare till Storage information container

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) lagrings informationen hämtades
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

Hämta antalet objekt på en lagrings behållare från svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar antalet objekt som lagras på en angiven lagrings behållare med värde storage_id som matchar en speciell format kod. Antalet objekt returneras i fältet: ux_host_class_pima_session_nb_objects i pima_sessions strukturen.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **storage_id**: ID för lagrings containern
- **object_format_code**: objekt format kod filter.

Objekt format koderna kan ha ett av följande värden.

| Objekt format kod               | Beskrivning   |     USBX-kod                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Odefinierat odefinierade icke-avbildnings objekt | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Associerings Association (t. ex. mapp) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Skript enhet-modell för skript | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Körbar enhets modell – en unik binär körbar fil | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Text text fil  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | HTML HyperText Markup Language-fil (text) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | DPOF Digital utskrifts order format fil (text) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | AIFF-ljudklipp  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | WAV-ljud klipp   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | MP3-ljud klipp   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | AVI-videoklipp   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | MPEG-videoklipp  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | ASF Microsoft Advanced Streaming format (video) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Odefinierat okänt bild objekt | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | EXIF/JPEG-utbytbart fil format, JEIDA standard | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | TIFF/EP tag Image File Format för elektronisk fotografering | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | Bild format för FlashPix-strukturerad lagring | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP Microsoft Windows-bitmappsfil | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | CIFF Canon Camera Image File Format | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Odefinierad reserverad |  |
| 0x3807                           | GIF-Graphics Interchange Format | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | JFIF JPEG File Interchange Format | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD PhotoCD-avbildning PAC | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | PICT QuickDraw bild format | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | PNG-Portable Network Graphics | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Odefinierad reserverad |   |
| 0x380D                           | TIFF-tagg bild fil format | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | TIFF/IT-tagga bild fil format för informations teknik (grafik) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | JP2 JPEG2000-format för original fil | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | JPX JPEG2000-utökat fil format | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Alla andra koder med MSN 0011 | Alla odefinierade reserverade för framtida användning |                                    |
| Alla övriga koder med MSN på 1011 | En leverantörsdefinierade typ som har angetts av leverantören: avbildning |                                    |

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

Hämta objekt referenser från svarare.

### <a name="prototype"></a>Prototyp

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

### <a name="description"></a>Beskrivning

Returnerar en matris med objekt referenser som finns i den lagrings behållare som anges av parametern storage_id. Om en sammanställd lista över alla butiker önskas, anges värdet 0xFFFFFFFF för värdet.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **object_handes_array**: matris där referenser returneras
- **object_handles_length**: matrisens längd
- **storage_id**: ID för lagrings containern
- **object_format_code**: formatera kod för objekt (se tabell för funktionen ux_host_class_pima_num_objects_get)
- **object_handle_association**: valfritt objekt kopplings värde

Objekt referens associationen kan vara något av värdet från tabellen nedan:

| AssociationCode                        | AssociationType      | Tolkning       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Undefined (Odefinierad)            | Undefined (Odefinierad)            |
| 0x0001                                 | GenericFolder        | Outnyttja               |
| 0x0002                                 | Artist                | Reserverat             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | Outnyttja               |
| 0x0005                                 | VerticalPanoramic    | Outnyttja               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | AncillaryData        | Undefined (Odefinierad)            |
| Alla andra värden med bit 15 inställt på 0  | Reserverat             | Undefined (Odefinierad)            |
| Alla värden med bit 15 inställt på 1        | Leverantörsdefinierade       | Leverantörsdefinierade       |

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

Hämta objekt informationen från svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar objekt information för en objekt referens.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **object_handle**: referens för objektet
- **objekt**: pekare till objekt information container

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

Skicka objekt informationen till responder.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Beskrivning

Den här funktionen skickar lagrings informationen för en lagrings behållare med värde storage_id. Initieraren bör använda det här kommandot innan du skickar ett objekt till den svarande.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-sessionen.
- **storage_id**: mål LAGRINGS-ID.
- **parent_object_id**: överordnad ObjectHandle i svarare där objektet ska placeras.
- **objekt**: pekar mot objekt informations behållare.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

Öppna ett objekt som lagras i svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Beskrivning

Den här funktionen öppnar ett objekt på den svarande innan den läses eller skrivs.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-sessionen.
- **object_handle**: objektets handtag.
- **objec**: pekar mot objekt informations behållare.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021)-objektet har redan öppnats.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

Hämta ett objekt som lagras i svarare.

### <a name="prototype"></a>Prototyp

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

### <a name="description"></a>Beskrivning

Den här funktionen hämtar ett objekt på den svarande.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **object_handle**: referens för objektet
- **objekt**: pekare till objekt information container
- **object_buffer**: adress för objekt data
- **object_buffer_length**: begärd objekt längd
- **object_actual_length**: den returnerade objekt längden

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) objektet överfördes
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) åtkomst till objekt nekad
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) överföring är ofullständig
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.
- **UX_TRANSFER_ERROR**: (0X23) överförings fel vid läsning av objekt

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

Skicka ett objekt som lagras i svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen skickar ett objekt till responder.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_sessio**: pekare till Pima-session
- **object_handle**: referens för objektet
- **objekt**: pekare till objekt information container
- **object_buffer**: adress för objekt data
- **object_buffer_length**: begärd objekt längd

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) åtkomst till objekt nekad
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) överföring är ofullständig
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.
- **UX_TRANSFER_ERROR**: (0X23) överförings fel vid skrivning av objekt

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

Hämta ett tumm-objekt som lagras i svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar ett tumme-objekt på den svarande.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-sessionen.
- **object_handle**: objektets handtag.
- **objekt**: pekar mot objekt informations behållare.
- **thumb_buffer**: adress för objekt data för tummen.
- **thumb_buffer_length**: den begärda längden för tumm-objektet.
- **thumb_actual_length**: längden på det returnerade objektet.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) åtkomst till objekt nekad.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) överföring är ofullständig.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.
- **UX_TRANSFER_ERROR**: (0X23) överförings fel vid läsning av objekt.

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

Ta bort ett objekt som lagras i svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Beskrivning

Den här funktionen tar bort ett objekt på den svarande

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-session
- **object_handle**: referens för objektet

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) objektet har tagits bort.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) Det går inte att ta bort objekt.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Stäng ett objekt som lagras i svars listan

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Beskrivning

Den här funktionen stänger ett objekt på den svarande.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **pima_session**: pekare till Pima-sessionen.
- **object_handle**: objektets handtag.
- **objekt**: pekar mot objekt.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) objektet stängdes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003)-sessionen har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023)-objektet har inte öppnats.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Läsa från det allmänna seriella gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen läser från det allmänna serie gränssnittet. Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **gser**: pekar mot instans av gser-klassen.
- **interface_index**: gränssnitts index som ska läsas från.
- **data_pointer**: pekar mot buffertstorleken för data nytto lasten.
- **requested_length**: längden som ska tas emot.
- **actual_length**: den längd som faktiskt mottagits.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, Läsning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Skriv till det allmänna seriella gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen skriver till det allmänna serie gränssnittet. Anropet blockeras och returneras bara när det uppstår ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **gser**: pekar mot instans av gser-klassen.
- **interface_index**: gränssnittet som ska skrivas.
- **data_pointer**: pekar mot buffertstorleken för data nytto lasten.
- **requested_length**: längden som ska skickas.
- **actual_length**: den längd som faktiskt har skickats.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_TRANSFER_TIMEOUT**: (0X5c) överförings tids gräns, skrivning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

Utföra en IOCTL-funktion på det allmänna seriella gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Beskrivning

Den här funktionen utför en angiven IOCTL-funktion till gser-gränssnittet. Anropet blockeras och returneras bara när det uppstår ett fel eller när kommandot har slutförts.

### <a name="parameters"></a>Parametrar

- **gser**: pekar mot instans av gser-klassen.
- **ioctl_function**: IOCTL-funktion som ska utföras. Se tabellen nedan för en av de tillåtna IOCTL-funktionerna.
- **parameter**: Pointerto en parameter som är unik för IOCTL

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) data överföringen har slutförts.
- **UX_MEMORY_INSUFFICIENT**: (0x12) det finns inte tillräckligt med minne.
- **UX_HOST_CLASS_UNKNOWN**: (0X59) fel klass instans
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) Okänd IOCTL-funktion.

### <a name="ioctl-functions"></a>IOCTL-funktioner

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

Börja ta emot på det allmänna seriella gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Beskrivning

Den här funktionen startar mottagningen på det generiska gränssnittet för seriella klassen. Den här funktionen tillåter icke-blockerande mottagning. När en buffert tas emot anropas en motringning i programmet.

### <a name="parameters"></a>Parametrar

- **gser** Pekare till gser-klass instansen.
- **gser_reception** Struktur som innehåller mottagnings parametrarna

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_UNKNOWN** (0X59) fel klass instans
- **UX_ERROR** (0x01)-fel

### <a name="example"></a>Exempel

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

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

Sluta ta emot det allmänna seriella gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Beskrivning

Den här funktionen stoppar mottagningen av gränssnittet för den allmänna seriella klassen.

### <a name="parameters"></a>Parametrar

- **gser** Pekare till gser-klass instansen.
- **gser_reception** Struktur som innehåller mottagnings parametrarna

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) data överföringen har slutförts.
- **UX_HOST_CLASS_UNKNOWN** (0X59) fel klass instans
- **UX_ERROR** (0x01)-fel

### <a name="example"></a>Exempel

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
