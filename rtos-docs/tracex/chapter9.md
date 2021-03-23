---
title: Kapitel 9 – Azure återställnings tider USBX trace Events
description: Det här kapitlet innehåller en beskrivning av de Azure återställnings tider USBX-händelser som visas av TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828350"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Kapitel 9 – Azure återställnings tider USBX trace Events

Det här kapitlet innehåller en beskrivning av de Azure återställnings tider USBX-händelser som visas av TraceX. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

Följande är en lista över USBX-händelser som visas av TraceX.

| Ikon                             | Innebörd                               |
| -------------------------------- | ------------------------------------- |
| ![Enhets klass C D C Aktivera ikon](./media/user-guide/usbx-events/image1.png)    | **Enhets klass CDC-aktivering** *(ux_device_class_cdc_activate)* |
| ![Enhets klass C D C inaktivera ikon](./media/user-guide/usbx-events/image2.png)    | **CDC-inaktive ring av enhets klass** *(ux_device_class_cdc_deactivate)* |
| ![Enhets klass C D C Läs ikon](./media/user-guide/usbx-events/image3.png)    | **Läsning av enhets klass CDC** *(ux_device_class_cdc_read)* |
| ![Enhets klass C D s Skriv ikon](./media/user-guide/usbx-events/image4.png)    | **Enhets klass CDC-skrivning** *(ux_device_class_cdc_write)* |
| ![Dpump Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image5.png)    | **Aktivering av enhets klass Dpump** *(ux_device_class_dpump_activate)* |
| ![Ikon för Dpump för enhets klass](./media/user-guide/usbx-events/image6.png)    | **Dpump för enhets klass** *(ux_device_class_dpump_deactivate)* |
| ![Läs ikon för enhets klassens Dpump](./media/user-guide/usbx-events/image7.png)    | **Läsning av enhets klassens Dpump** *(ux_device_class_dpump_read)* |
| ![Dpump Skriv ikon för enhets klass](./media/user-guide/usbx-events/image8.png)    | **Skrivning av enhets klass Dpump** *(ux_device_class_dpump_write)* |
| ![Ikon för HID-aktivering i enhets klass](./media/user-guide/usbx-events/image9.png)    | **HID-aktivering för enhets klass** *(ux_device_class_hid_activate)* |
| ![Ikon för HID-inaktivera enhets klass](./media/user-guide/usbx-events/image10.png)    | **HID-inaktive ring av enhets klass** *(ux_device_class_hid_deactivate)* |
| ![Ikon för att skicka HID-beskrivning för enhets klass](./media/user-guide/usbx-events/image11.png)    | **Skicka HID-beskrivning för enhets klass** *(ux_device_class_hid_descriptor_send)* |
| ![Ikonen Hämta ikon för enhets klassens HID-händelse](./media/user-guide/usbx-events/image12.png)    | **Hämta HID-händelse för enhets klass** *(ux_device_class_hid_event_get)* |
| ![Ikon uppsättnings ikon för HID-händelseloggen i enhets klass](./media/user-guide/usbx-events/image13.png)    | **HID-händelse uppsättning för enhets klass** *(ux_device_class_hid_event_set)* |
| ![Ikonen Hämta ikon för enhets klassens HID-rapport](./media/user-guide/usbx-events/image14.png)    | **Hämta HID-rapport för enhets klass** *(ux_device_class_hid_report_get)* |
| ![Ikon för HID-rapport för enhets klass](./media/user-guide/usbx-events/image15.png)    | **HID-rapport uppsättning i enhets klass** *(ux_device_class_hid_report_set)* |
| ![Pima Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image16.png)    | **Aktivering av enhets klass Pima** *(ux_device_class_pima_activate)* |
| ![Ikon för Pima för enhets klass](./media/user-guide/usbx-events/image17.png)    | **Pima för enhets klass** *(ux_device_class_pima_deactivate)* |
| ![Enhets klass Pima enhets information skicka ikon](./media/user-guide/usbx-events/image18.png)    | **Skicka enhets information i enhets klass Pima** *(ux_device_class_pima_device_info_send)* |
| ![Enhets klass Pima händelse Hämta ikon](./media/user-guide/usbx-events/image19.png)    | **Enhets klass Pima Event get** *(ux_device_class_pima_event_get)* |
| ![Enhets klass Pima händelse uppsättnings ikon](./media/user-guide/usbx-events/image20.png)    | **Pima händelse uppsättning** *(Ux_device_class_pima_event_set)* för enhets klass |
| ![Enhets klass Pima objekt Lägg till ikon](./media/user-guide/usbx-events/image21.png)    | **Enhets klass Pima objekt Lägg till** *(ux_device_class_pima_object_add)* |
| ![Enhets klass Pima objekt data hämta ikon](./media/user-guide/usbx-events/image22.png)    | **Enhets klass Pima objekt data hämta** *(ux_device_class_pima_object_data_get)* |
| ![Ikon för att skicka Pima objekt data i enhets klass](./media/user-guide/usbx-events/image23.png)    | **Skicka objekt data från enhets klass Pima** *(ux_device_class_pima_object_data_send)* |
| ![Pima objekt borttagnings ikon för enhets klass](./media/user-guide/usbx-events/image24.png)    | **Enhets klass Pima objekt borttagning** *(ux_device_class_pima_object_delete)* |
| ![Skicka ikon för Pima objekt i enhets klass](./media/user-guide/usbx-events/image25.png)    | **Pima objekt i enhets klass hanterar skicka** *(ux_device_class_pima_object_handles_send)* |
| ![Enhets klass Pima objekt information Hämta ikon](./media/user-guide/usbx-events/image26.png)    | **Enhets klass Pima objekt information get** *(ux_device_class_pima_object_info_get)* |
| ![Skicka ikon för Pima objekt information i enhets klass](./media/user-guide/usbx-events/image27.png)    | **Skicka Pima objekt information** *(Ux_device_class_pima_object_info_send)* i enhets klass |
| ![Enhets klass Pima objekt nummer skicka ikon](./media/user-guide/usbx-events/image28.png)    | Skicka *(ux_device_class_pima_objects_number_send)* **Pima objekt nummer i enhets klass** |
| ![Enhets klass Pima del objekt data hämta ikon](./media/user-guide/usbx-events/image29.png)    | **Enhets klass Pima del objekt data hämta** *(ux_device_class_pima_partial_object_data_get)* |
| ![Ikon för Pima svars sändning i enhets klass](./media/user-guide/usbx-events/image30.png)    | **Pima för enhets klassens svar** *(ux_device_class_pima_response_send)*|
| ![Enhets klass Pima Storage I D-skicka ikon](./media/user-guide/usbx-events/image31.png)    | **Enhets klass Pima lagrings-ID skicka** *(ux_device_class_pima_storage_id_send)* |
| ![Enhets klass Pima Storage information skicka ikon](./media/user-guide/usbx-events/image32.png)    | **Sändning av Pima Storage-information i enhets klass** *(ux_device_class_pima_storage_info_send)* |
| ![Enhets klass R N D I S Aktivera ikon](./media/user-guide/usbx-events/image33.png)    | **Aktivering av enhets klass RNDIS** *(ux_device_class_rndis_activate)* |
| ![Ikonen enhets klass R N D I S inaktivera](./media/user-guide/usbx-events/image34.png)    | **RNDIS för enhets klass** *(ux_device_class_rndis_deactivate)* |
| ![Enhets klass R N D I S meddelande Behåll Aliveicon](./media/user-guide/usbx-events/image35.png)    | **Enhets klass RNDIS meddelande Keep Alive** *(ux_device_class_rndis_msg_keep_alive)* |
| ![Ikon för enhets klass R N D N D I S](./media/user-guide/usbx-events/image36.png)    | **RNDIS meddelande fråga för enhets klass** *(ux_device_class_rndis_msg_query)* |
| ![Enhets klass R N D I S ikon för meddelande återställning](./media/user-guide/usbx-events/image37.png)    | **RNDIS meddelande återställning för enhets klass** *(ux_device_class_rndis_msg_reset)* |
| ![Ikon för enhets klass R N D N D I S](./media/user-guide/usbx-events/image38.png)    | **RNDIS meddelande uppsättning för enhets klass** *(ux_device_class_rndis_msg_set)* |
| ![Enhets klass R N D N D I S paket mottagnings ikon](./media/user-guide/usbx-events/image39.png)    | **Mottagning av enhets klassens RNDIS-paket** *(ux_device_class_rndis_packet_receive)* |
| ![Enhets klass R N D I S paket sändnings ikon](./media/user-guide/usbx-events/image40.png)    | **RNDIS Packet överföring i enhets klass** *(ux_device_class_rndis_packet_transmit)* |
| ![Aktiverings ikon för enhets klass lagring](./media/user-guide/usbx-events/image41.png)    | **Aktivering av enhets klass lagring** *(ux_device_class_storage_activate)* |
| ![Ikon för enhets klassens lagrings inaktive rad](./media/user-guide/usbx-events/image42.png)    | **Inaktive ring av enhets klass lagring** *(ux_device_class_storage_deactivate)* |
| ![Ikon för lagrings format för enhets klass](./media/user-guide/usbx-events/image43.png)    | **Lagrings format för enhets klass** *(ux_device_class_storage_format)* |
| ![Ikon för enhets klass lagrings förfrågan](./media/user-guide/usbx-events/image44.png)    | **Förfrågan om enhets klass lagring** *(ux_device_class_storage_inquiry)* |
| ![Enhets klassens lagrings läge Välj ikon](./media/user-guide/usbx-events/image45.png)    | **Val av enhets klassens lagrings läge** *(ux_device_class_storage_mode_select)* |
| ![Ikon för lagrings läge i enhets klass](./media/user-guide/usbx-events/image46.png)    | **Enhets klassens lagrings läge Sense** *(ux_device_class_storage_mode_sense)* |
| ![Enhets klass lagring förhindra att ikonen borttagning av media](./media/user-guide/usbx-events/image47.png)    | **Enhets klass lagring förhindra borttagning av media** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Läs ikon för enhets klass lagring](./media/user-guide/usbx-events/image48.png)    | **Läsning av enhets klass lagring** *(ux_device_class_storage_read)* |
| ![Enhets klass lagring Läs kapacitets ikon](./media/user-guide/usbx-events/image49.png)    | **Läs kapacitet för enhets klass lagring** *(ux_device_class_storage_read_capacity)* |
| ![Kapacitets ikon för Läs format för enhets klass lagring](./media/user-guide/usbx-events/image50.png)    | **Kapacitet för läsning av enhets klass lagring** *(ux_device_class_storage_read_format_capacity)* |
| ![Enhets klass lagring läsa innehålls förtecknings ikon](./media/user-guide/usbx-events/image51.png)    | **Läsa innehålls förteckning för enhets klass lagring** *(ux_device_class_storage_read_toc)* |
| ![Ikon för enhets klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image52.png)    | **Enhets klass Storage-begäran Sense** *(ux_device_class_storage_request_sense)* |
| ![Start stopps ikon för enhets klass lagring](./media/user-guide/usbx-events/image53.png)    | **Start stopp för enhets klass lagring** *(ux_device_class_storage_start_stop)* |
| ![Ikon för lagrings test för enhets klass](./media/user-guide/usbx-events/image54.png)    | **Test av enhets klass lagring är klar** *(ux_device_class_storage_test_ready)* |
| ![Enhets klass lagring verifiera ikon](./media/user-guide/usbx-events/image55.png)    | **Verifiera lagring av enhets klass** *(ux_device_class_storage_verify)* |
| ![Skriv ikon för enhets klass lagring](./media/user-guide/usbx-events/image56.png)    | **Lagrings skrivning av enhets klass** *(ux_device_class_storage_write)* |
| ![Alternativ inställnings ikon för enhets stack](./media/user-guide/usbx-events/image57.png)    | **Alternativ inställning för enhets stack Hämta** *(ux_device_stack_alternate_setting_get)* |
| ![Ikon för alternativ inställnings uppsättning för enhets stack](./media/user-guide/usbx-events/image58.png)    | **Alternativ inställnings uppsättning för enhets stack** *(ux_device_stack_alternate_setting_set)* |
| ![Enhets Stack klass register ikon](./media/user-guide/usbx-events/image59.png)    | **Enhets Stack klass register** *(ux_device_stack_class_register)* |
| ![Enhets stack rensa funktions ikon](./media/user-guide/usbx-events/image60.png)    | **Rensnings funktion för enhets stack** *(ux_device_stack_clear_feature)* |
| ![Hämta ikon för enhets stack konfiguration](./media/user-guide/usbx-events/image61.png)    | **Hämta enhets stack konfiguration** *(ux_device_stack_configuration_get)* |
| ![Ikon för enhets stack konfigurations uppsättning](./media/user-guide/usbx-events/image62.png)    | **Konfigurations uppsättning för enhets stack** *(ux_device_stack_configuration_set)* |
| ![Enhets stackens anslutnings ikon](./media/user-guide/usbx-events/image63.png)    | **Enhets stack anslutning** *(ux_device_stack_connect)* |
| ![Ikon för att skicka enhets stack Beskrivning](./media/user-guide/usbx-events/image64.png)    | **Skicka enhets Stacks Beskrivning** *(ux_device_stack_descriptor_send)* |
| ![Ikon för enhets stack från koppling](./media/user-guide/usbx-events/image65.png)    | **Enhets stack från koppling** *(ux_device_stack_disconnect)* |
| ![Ikon för enhets stackens slut punkts bås](./media/user-guide/usbx-events/image66.png)    | **Enhets stackens slut punkts ficka** *(ux_device_stack_endpoint_stall)* |
| ![Enhets stack Hämta status ikon](./media/user-guide/usbx-events/image67.png)    | **Enhets stack Hämta status** *(ux_device_stack_get_status)* |
| ![Aktiverings ikon för värd för enhets stack](./media/user-guide/usbx-events/image68.png)    | **Aktivering av enhets stack värd** *(ux_device_stack_host_wakeup)* |
| ![Ikon för enhets stack initierare](./media/user-guide/usbx-events/image69.png)    | **Initiera enhets stack** *(ux_device_stack_initialize)* |
| ![Borttagnings ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image70.png)    | **Borttagning av enhets Stacks gränssnitt** *(ux_device_stack_interface_delete)* |
| ![Hämta ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image71.png)    | **Hämta enhets stack gränssnitt** *(ux_device_stack_interface_get)* |
| ![Ikon för enhets stackens gränssnitts uppsättning](./media/user-guide/usbx-events/image72.png)    | **Enhets stack gränssnitts uppsättning** *(ux_device_stack_interface_set)* |
| ![Funktions ikon för enhets stack uppsättning](./media/user-guide/usbx-events/image73.png)    | **Enhets stack uppsättnings funktion** *(ux_device_stack_set_feature)* |
| ![Avbrotts ikon för enhets stack överföring](./media/user-guide/usbx-events/image74.png)    | **Avbrotts överföring av enhets stack** *(ux_device_stack_transfer_abort)* |
| ![* Ikon för enhets stacken överför alla begär Anden Avbryt](./media/user-guide/usbx-events/image75.png)    | **Enhets stack överför alla begäran om att avbryta begäran** *(ux_device_stack_transfer_all_request_abort)* |
| ![Ikon för begäran om enhets stack-överföring](./media/user-guide/usbx-events/image76.png)    | **Begäran om enhets stack överföring** *(ux_device_stack_transfer_request)* |
| ![Asix Aktivera ikon för värd klass](./media/user-guide/usbx-events/image77.png)    | **Aktivering av värd klass Asix** *(ux_host_class_asix_activate)* |
| ![Asix-ikon för värd klass](./media/user-guide/usbx-events/image78.png)    | **Asix inaktive ring av värd klass** *(ux_host_class_asix_deactivate)* |
| ![Asix för värd klassens avbrotts meddelande](./media/user-guide/usbx-events/image79.png)    | **Avbrotts meddelande för värd klass Asix** *(ux_host_class_asix_interrupt_notification)* |
| ![Läs ikon för värd klassen Asix](./media/user-guide/usbx-events/image80.png)    | **Läsning av värd klass Asix** *(ux_host_class_asix_read)* |
| ![Asix Skriv ikon för värd klass](./media/user-guide/usbx-events/image81.png)    | **Skrivning av värd klass Asix** *(ux_host_class_asix_write)* |
| ![Ikon för ljud aktivering i värd klass](./media/user-guide/usbx-events/image82.png)    | **Ljud aktivering av värd klass** *(ux_host_class_audio_activate)* |
| ![Ikonen Hämta ljud kontroll värde i värd klass](./media/user-guide/usbx-events/image83.png)    | **Hämta ljud kontroll värde i värd klass** *(ux_host_class_audio_control_value_get)* |
| ![Ikon för ljud kontroll värde för värd klass](./media/user-guide/usbx-events/image84.png)    | **Ljud kontroll värdes uppsättning i värd klass** *(ux_host_class_audio_control_value_set)* |
| ![Ikon för ljud inaktive ring av värd klass](./media/user-guide/usbx-events/image85.png)    | **Ljud inaktive ring av värd klass** *(ux_host_class_audio_deactivate)* |
| ![Ljud läsnings ikon för värd klass](./media/user-guide/usbx-events/image86.png)    | **Ljud läsning av värd klass** *(ux_host_class_audio_read)* |
| ![Exempel på hämtnings ikon för värd klassens ljud strömning](./media/user-guide/usbx-events/image87.png)    | **Exempel på ljud uppspelning av värd klass för hämtning** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Ikon för samplings uppsättning för värd klassens ljud strömning](./media/user-guide/usbx-events/image88.png)    | **Provtagnings uppsättning för ljud strömning i värd klass** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Ljud Skriv ikon för värd klass](./media/user-guide/usbx-events/image89.png)    | **Ljud skrivning av värd klass** *(ux_host_class_audio_write)* |
| ![Värd klass C D C A C M Aktivera ikon](./media/user-guide/usbx-events/image90.png)    | **Värd klass CDC ACM Activate** *(ux_host_class_cdc_acm_activate)* |
| ![Värd klass C D C A C M inaktivera ikon](./media/user-guide/usbx-events/image91.png)    | **Värd klass CDC ACM-inaktive rad** *(ux_host_class_cdc_acm_deactivate)* |
| ![Värd klass C D A C M I O C T L i pipe-ikon](./media/user-guide/usbx-events/image92.png)    | **Värd klass CDC ACM IOCTL abort i pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Värd klass C D C A C M I O C T L ta bort pipe-ikon](./media/user-guide/usbx-events/image93.png)    | **Värd klass CDC ACM IOCTL avbryter pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Värd klass C D C A C M I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image94.png)    | **Värd klass CDC ACM IOCTL get enhets status** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Värd klass C D C A C M I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image95.png)    | **Värd klass CDC ACM IOCTL get line** *-kodning (ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Värd klass C D C A C M I O C T L ikon för återanrop i meddelande](./media/user-guide/usbx-events/image96.png)    | **Värd klass CDC ACM IOCTL Notification motringning** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Värd klass C D C A C M I O C T L-ikonen skicka rast](./media/user-guide/usbx-events/image97.png)    | **Värd klass CDC ACM IOCTL Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Värd klass C D C A C M I O C T L ange rad kodnings ikon](./media/user-guide/usbx-events/image98.png)    | **Värd klass CDC ACM IOCTL set line** *-kodning (ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Värd klass C D C A C M I O C T L ikon för ange linje tillstånd](./media/user-guide/usbx-events/image99.png)    | **Värd klass CDC ACM IOCTL set line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Värd klass C D A C M Läs ikon](./media/user-guide/usbx-events/image100.png)    | **Värd klass CDC ACM Read** *(ux_host_class_cdc_acm_read)* |
| ![Start ikon för värd klass C D A C M](./media/user-guide/usbx-events/image101.png)    | **Start av värd klass CDC-ACM** *(ux_host_class_cdc_acm_reception_start)* |
| ![Svars ikon för värd klass C D A C M](./media/user-guide/usbx-events/image102.png)    | **ACM för värd klass CDC-mottagning** *(ux_host_class_cdc_acm_reception_stop)* |
| ![Värd klass C D A C M Skriv ikon](./media/user-guide/usbx-events/image103.png)    | **Värd klass CDC ACM Write** *(ux_host_class_cdc_acm_write)* |
| ![Dpump Aktivera ikon för värd klass](./media/user-guide/usbx-events/image104.png)    | **Aktivering av värd klass Dpump** *(ux_host_class_dpump_activate)* |
| ![Dpump-ikon för värd klass](./media/user-guide/usbx-events/image105.png)    | **Dpump inaktive ring av värd klass** *(ux_host_class_dpump_deactivate)* |
| ![Läs ikon för värd klassen Dpump](./media/user-guide/usbx-events/image106.png)    | **Läsning av värd klass Dpump** *(ux_host_class_dpump_read)* |
| ![Dpump Skriv ikon för värd klass](./media/user-guide/usbx-events/image107.png)    | **Skrivning av värd klass Dpump** *(ux_host_class_dpump_write)* |
| ![Ikon för HID-aktivering i värd klass](./media/user-guide/usbx-events/image108.png)    | **HID-aktivering för värd klass** *(ux_host_class_hid_activate)* |
| ![Register ikon för HID-klient för värd klass](./media/user-guide/usbx-events/image109.png)    | **HID-klient register för värd klass** *(ux_host_class_hid_client_register)* |
| ![Ikon för HID-inaktivera värd klass](./media/user-guide/usbx-events/image110.png)    | **HID-inaktive ring av värd klass** *(ux_host_class_hid_deactivate)* |
| ![Ikon för HID-inaktivitet i värd klass](./media/user-guide/usbx-events/image111.png)    | **HID Idle-inaktivitet i värd klass** *(ux_host_class_hid_idle_get)* |
| ![Ikon för HID inaktive rad värd klass](./media/user-guide/usbx-events/image112.png)    | **HID Idle-uppsättning** *(Ux_host_class_hid_idle_set)* för värd klass |
| ![Ikon för HID-tangentbordet för värd klass](./media/user-guide/usbx-events/image113.png)    | **Aktivera HID-tangentbordet för värd klass** *(ux_host_class_hid_keyboard_activate)* |
| ![Ikonen värd klass HID tangent bords inaktive ring](./media/user-guide/usbx-events/image114.png)    | **HID-tangentbordsmus för värd klass** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Aktivera ikon för HID-mus i värd klass](./media/user-guide/usbx-events/image115.png)    | **Aktivera HID-mus för värd klass** *(ux_host_class_hid_mouse_activate)* |
| ![Värd klass HID-mus inaktivera ikon](./media/user-guide/usbx-events/image116.png)    | **Värd klass HID-mus inaktive rad** *(ux_host_class_hid_mouse_deactivate)* |
| ![Ikonen aktivera HID-fjärrstyrning i värd klass](./media/user-guide/usbx-events/image117.png)    | **Aktivera HID-fjärrstyrning av värd klass** *(ux_host_class_hid_remote_control_activate)* |
| ![Ikon för HID-fjärrstyrning av värd klass](./media/user-guide/usbx-events/image118.png)    | **HID-fjärrstyrning av värd klass** *(ux_host_class_hid_remote_control_deactivate)* |
| ![Ikon för Hämta värd klass HID-rapport](./media/user-guide/usbx-events/image119.png)    | **Hämta HID-rapport för värd klass** *(ux_host_class_hid_report_get)* |
| ![Ikon för HID-rapport för värd klass](./media/user-guide/usbx-events/image120.png)    | **HID-rapport uppsättning för värd klass** *(ux_host_class_hid_report_set)* |
| ![Aktivera ikon för värd klassens hubb](./media/user-guide/usbx-events/image121.png)    | **Aktivera värd klass hubb** *(ux_host_class_hub_activate)* |
| ![Identifiera ikon för värd klassens hubb ändring](./media/user-guide/usbx-events/image122.png)    | **Identifiera ändring av värd klassens hubb** *(ux_host_class_hub_change_detect)* |
| ![* Ikon för att inaktivera värd Klasss hubb](./media/user-guide/usbx-events/image123.png)    | **Inaktive ring av värd klassens hubb** *(ux_host_class_hub_deactivate)* |
| ![Ikon för att ändra anslutnings process för värd klassens hubb port](./media/user-guide/usbx-events/image124.png)    | **Anslutnings process för port ändring i värd klass** *(ux_host_class_hub_port_change_connection_process)* |
| ![Aktivera process ikon för värd klassens hubb port ändring](./media/user-guide/usbx-events/image125.png)    | **Aktiverings process för port ändring i värd klass** *(ux_host_class_hub_port_change_enable_process)* |
| ![Port ändring över ikon för värd Klasss hubb över den aktuella process ikonen](./media/user-guide/usbx-events/image126.png)    | **Port ändring i värd klassens hubb över den aktuella processen** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Ikon för ändrings process för värd klassens Hubbs port](./media/user-guide/usbx-events/image127.png)    | **Återställnings process för port ändring av värd klass** *(ux_host_class_hub_port_change_reset_process)* |
| ![Ikon för att inaktivera process klassens hubb port ändring](./media/user-guide/usbx-events/image128.png)    | Inaktive ring av **värd klassens nav port ändrings process** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Pima Aktivera ikon för värd klass](./media/user-guide/usbx-events/image129.png)    | **Aktivering av värd klass Pima** *(ux_host_class_prima_activate)* |
| ![Pima-ikon för värd klass](./media/user-guide/usbx-events/image130.png)    | **Pima inaktive ring av värd klass** *(ux_host_class_pima_deactivate)* |
| ![Hämta ikon för värd klassens Pima enhets information](./media/user-guide/usbx-events/image131.png)    | **Hämta Pima enhets information för värd klass** *(ux_host_class_pima_device_info_get)* |
| ![Enhets återställnings ikon för värd klass Pima](./media/user-guide/usbx-events/image132.png)    | **Enhets återställning för Pima av värd klass** *(ux_host_class_pima_device_reset)* |
| ![Meddelande ikon för värd klass Pima](./media/user-guide/usbx-events/image133.png)    | **Pima-meddelande för värd klass** *(ux_host_class_pima_notification)* |
| ![Ikon för Pima för värd klassens antal objekt](./media/user-guide/usbx-events/image134.png)    | **Pima antal objekt för värd klass hämtning** *(ux_host_class_pima_num_objects_get)* |
| ![Ikonen Stäng Pima objekt i värd klass](./media/user-guide/usbx-events/image135.png)    | **Pima objekt stängning för värd klass** *(ux_host_class_pima_object_close)* |
| ![Objekt kopierings ikon för värd klass Pima](./media/user-guide/usbx-events/image136.png)    | **Objekts kopia av värd klassens Pima** *(ux_host_class_pima_object_copy)* |
| ![Pima objekt borttagnings ikon för värd klass](./media/user-guide/usbx-events/image137.png)    | **Ta bort värd klass Pima objekt** *(ux_host_class_pima_object_delete)* |
| ![Pima objekt Hämta ikon för värd klass](./media/user-guide/usbx-events/image138.png)    | **Hämta värd klass Pima objekt** *(ux_host_class_pima_object_get)* |
| ![Hämta ikon för värd klassens Pima objekt information](./media/user-guide/usbx-events/image139.png)    | **Hämta Pima för värd klassens objekt information** *(ux_host_class_pima_object_info_get)* |
| ![Skicka ikon för Pima objekt information i värd klass](./media/user-guide/usbx-events/image140.png)    | **Sändning av Pima objekt information i värd klass** *(ux_host_class_pima_object_info_send)* |
| ![Ikon för flytt av Pima objekt i värd klass](./media/user-guide/usbx-events/image141.png)    | **Flytt av Pima objekt i värd klass** *(ux_host_class_pima_object_move)* |
| ![Ikon för att skicka Pima objekt i värd klass](./media/user-guide/usbx-events/image142.png)    | **Skicka Pima objekt i värd klass** *(ux_host_class_pima_object_send)* |
| ![Avbrotts ikon för Pima objekt överföring i värd klass](./media/user-guide/usbx-events/image143.png)    | **Avbryt Pima objekt överföring i värd klass** *(ux_host_class_object_transfer_abort)* |
| ![Läs ikon för värd klassen Pima](./media/user-guide/usbx-events/image144.png)    | **Läsning av värd klass Pima** *(ux_host_class_pima_read)* |
| ![Ikon för Pima-begäran i värd klass](./media/user-guide/usbx-events/image145.png)    | **Pima-begäran för värd klass Avbryt** *(ux_host_class_pima_request_cancel)* |
| ![Pima för värd klassens stängnings ikon](./media/user-guide/usbx-events/image146.png)    | **Pima-session för värd klass stängs** *(ux_host_class_pima_session_close)* |
| ![Öppna Pima-ikonen för värd klassens session](./media/user-guide/usbx-events/image147.png)    | **Pima-session för värd klass öppen** *(ux_host_class_pima_session_open)* |
| ![Pima lagrings-ID Hämta ikon för värd klass](./media/user-guide/usbx-events/image148.png)    | **Pima lagrings-ID: n** *(Ux_host_class_pima_storage_ids_get)* för värd klass |
| ![Pima Storage information get-ikon i värd klass](./media/user-guide/usbx-events/image149.png)    | **Pima Storage information get** *(Ux_host_class_pima_storage_info_get)* i värd klass |
| ![Ikon för Pima för värd klass](./media/user-guide/usbx-events/image150.png)    | **Pima-skjutreglage för värd klass** *(ux_host_class_pima_thumb_get)* |
| ![Pima Skriv ikon för värd klass](./media/user-guide/usbx-events/image151.png)    | **Skrivning av värd klass Pima** *(ux_host_class_pima_write)* |
| ![Aktivera ikon för värd klass skrivare](./media/user-guide/usbx-events/image152.png)    | **Aktivera värd klass skrivare** *(ux_host_class_printer_activate)* |
| ![Ikon för att inaktivera värd klass skrivare](./media/user-guide/usbx-events/image153.png)    | **Inaktive ring av värd klass skrivare** *(ux_host_class_printer_deactivate)* |
| ![Hämta ikon för värd klassens skrivar namn](./media/user-guide/usbx-events/image154.png)    | **Skrivar namn för värd klass Hämta** *(ux_host_class_printer_name_get)* |
| ![Läs ikon för värd klass skrivare](./media/user-guide/usbx-events/image155.png)    |  **Läsning av värd klass skrivare** *(ux_host_class_printer_read)* |
| ![Ikon för mjuk återställning av värd klass skrivare](./media/user-guide/usbx-events/image156.png)    | **Mjuk återställning av värd klass skrivare** *(ux_host_class_printer_soft_reset)* |
| ![Ikon för Hämta värd klass skrivar status](./media/user-guide/usbx-events/image157.png)    | **Hämta status för värd klass skrivare** *(ux_host_class_printer_status_get)* |
| ![Skriv ikon för värd klass skrivare](./media/user-guide/usbx-events/image158.png)    | **Skrivning av värd klass skrivare** *(ux_host_class_printer_write)* |
| ![Prolific Aktivera ikon för värd klass](./media/user-guide/usbx-events/image159.png)    | **Aktivering av värd klass Prolific** *(ux_host_class_prolific_activate)* |
| ![Prolific-ikon för värd klass](./media/user-guide/usbx-events/image160.png)    | **Prolific inaktive ring av värd klass** *(ux_host_class_prolific_deactivate)* |
| ![Prolific för värd klass I O C T L Avbryt i pipe-ikon](./media/user-guide/usbx-events/image161.png)    | **Värd klass Prolific IOCTL Avbryt i pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Prolific för värd klass I O C T L ta bort pipe-ikon](./media/user-guide/usbx-events/image162.png)    | **Prolific för värd klass IOCTL avbryter pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Prolific för värd klass I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image163.png)    | **Värd klass Prolific IOCTL get enhets status** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![Prolific för värd klass I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image164.png)    | **Prolific för värd klass IOCTL get line-kodning** *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Prolific för värd klass I O C T L ta bort ikon](./media/user-guide/usbx-events/image165.png)    | **Prolific IOCTL-rensning i värd klass** *(ux_host_class_prolific_ioctl_purge)* |
| ![Enhets status ändrings ikon för värd klass Prolific I O d T L](./media/user-guide/usbx-events/image166.png)    | **Status ändring för Prolific IOCTL-rapport enhets status i värd klass** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Prolific för värd klass I O C T L](./media/user-guide/usbx-events/image167.png)    | **Sändning av värd klass Prolific IOCTL skicka rast** *(ux_host_class_prolific_ioctl_send_break)* |
| ![Prolific för värd klass I O C T L ange rad kodnings ikon](./media/user-guide/usbx-events/image168.png)    | **Prolific för värd klassens IOCTL-uppsättning** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Ikon för värd klass Prolific I O C T L](./media/user-guide/usbx-events/image169.png)    | **Prolific IOCTL ange linje tillstånd** *(Ux_host_class_prolific_ioctl_set_line_state)* i värd klass |
| ![Läs ikon för värd klassen Prolific](./media/user-guide/usbx-events/image170.png)    | **Läsning av värd klass Prolific** *(ux_host_class_prolific_read)* |
| ![Start ikon för Prolific mottagning i värd klass](./media/user-guide/usbx-events/image171.png)    | **Start av värd klass Prolific mottagning** *(ux_host_class_prolific_reception_start)* |
| ![Stopp ikon för Prolific för värd klass](./media/user-guide/usbx-events/image172.png)    | **Prolific för värd klassens mottagnings stopp** *(ux_host_class_prolific_reception_stop)* |
| ![Prolific Skriv ikon för värd klass](./media/user-guide/usbx-events/image173.png)    | **Skrivning av värd klass Prolific** *(ux_host_class_prolific_write)* |
| ![Aktivera ikon för värd klass lagring](./media/user-guide/usbx-events/image174.png)    | **Aktivering av värd klass lagring** *(ux_host_class_storage_activate)* |
| ![Ikon för värd klass lagrings inaktive ring](./media/user-guide/usbx-events/image175.png)    | **Inaktive ring av värd klass lagring** (*ux_host_class_storage_deactivate)* |
| ![Ikon för Hämta värd klass lagrings medie kapacitet](./media/user-guide/usbx-events/image176.png)    | **Hämtning av värd klass lagrings medie kapacitet** *(ux_host_class_storage_media_capacity_get)* |
| ![Ikon för Hämta kapacitet för värd klass lagrings medie format](./media/user-guide/usbx-events/image177.png)    | **Hämtnings kapacitet för värd klass lagrings medie format** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Monterings ikon för värd klass lagrings medium](./media/user-guide/usbx-events/image178.png)    | **Värd klass lagrings medie montering** (ux_host_class_storage_media_mount) * |
| ![Öppnings ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image179.png)    | **Värd klass lagrings medium öppet** *(ux_host_class_storage_media_open)* |
| ![Läs ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image180.png)    | **Läsning av värd klassens lagrings medium** *(ux_host_class_storage_media_read)* |
| ![Skriv ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image181.png)    | **Skrivning av värd klass lagrings medium** *(ux_host_class_storage_media_write)* |
| ![Ikon för värd klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image182.png)    | **Sense-begäran för värd klass lagring** *(ux_host_class_storage_request_sense)* |
| ![Start stopp ikon för värd klass lagring](./media/user-guide/usbx-events/image183.png)    | **Start stopp för värd klass lagring** *(ux_host_class_storage_start_stop)* |
| ![Test ikon för värd klassens lagrings enhet](./media/user-guide/usbx-events/image184.png)    | **Redo test för värd klass lagrings enhet** *(ux_host_class_storage_activate)* |
| ![Ikon för att skapa värd Stack klass instans](./media/user-guide/usbx-events/image185.png)    | **Värd Stack klass instans skapa** *(ux_host_stack_class_instance_create)* |
| ![Ikon för att förstöra värd Stack klass instans](./media/user-guide/usbx-events/image186.png)    | **Förstöring av värd Stack klass instans** *(ux_host_stack_class_instance_destroy)* |
| ![Borttagnings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image187.png)    | **Ta bort värd stack konfiguration** *(ux_host_stack_configuration_delete)* |
| ![Uppräknings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image188.png)    | **Uppräkning av värd stack konfiguration** *(ux_host_stack_configuration_enumerate)* |
| ![Ikon för att skapa värd stack konfigurations instans](./media/user-guide/usbx-events/image189.png)    | **Skapa värd stack konfigurations instans** *(ux_host_stack_configuration_instance_create)* |
| ![Borttagnings ikon för värd Stacks konfigurations instans](./media/user-guide/usbx-events/image190.png)    | **Borttagning av värd Stacks konfigurations instans** *(ux_host_stack_configuration_instance_delete)* |
| ![Ikon för konfigurations uppsättning för värd stack](./media/user-guide/usbx-events/image191.png)    | **Konfigurations uppsättning för värd stack** *(ux_host_stack_configuration_set)* |
| ![Ikon för värd stack enhetens adress uppsättning](./media/user-guide/usbx-events/image192.png)    | **Adress uppsättning för värd stack enhet** *(ux_host_stack_device_set)* |
| ![Hämta ikon för värd stack enhets konfiguration](./media/user-guide/usbx-events/image193.png)    | **Hämtning av värd stack enhets konfiguration** *(ux_host_stack_device_configuration_get)* |
| ![Konfiguration av värd stack enhets konfiguration Välj ikon](./media/user-guide/usbx-events/image194.png)    | **Konfiguration av värd stack enhets konfiguration Välj** *(ux_host_stack_device_configuration_select)* |
| ![Läs ikon för värd stack enhets Beskrivning](./media/user-guide/usbx-events/image195.png)    | **Läsning av värd stack enhets Beskrivning** *(ux_host_stack_device_descriptor_read)* |
| ![Hämta ikon för värd stack enhet](./media/user-guide/usbx-events/image196.png)    | **Värd stack enhet Hämta** (ux_host_stack_device_get) |
| ![Ikon för att ta bort värd stack enhet](./media/user-guide/usbx-events/image197.png)    | **Ta bort värd stack enhet** (ux_host_stack_device_get) |
| ![Ikon för värd stack för enhets resurs](./media/user-guide/usbx-events/image198.png)    | **Värd stack enhets resurs kostnads fritt** (ux_host_stack_device_resource_free) |
| ![Ikon för att skapa värd stack slut punkts instans](./media/user-guide/usbx-events/image199.png)    | **Skapa värd stack slut punkts instans** (ux_host_stack_endpoint_instance_create) |
| ![Borttagnings ikon för värd stack slut punkts instans](./media/user-guide/usbx-events/image200.png)    | **Borttagning av värd stack slut punkts instans** (ux_host_stack_endpoint_instance_delete) |
| ![Ikon för återställning av värd stack slut punkt](./media/user-guide/usbx-events/image201.png)    | **Återställning av värd stack slut punkt** (ux_host_stack_endpoint_reset) |
| ![Avbryt ikon för värd stack slut punkts överföring](./media/user-guide/usbx-events/image202.png)    | **Avbryt överföring av värd stack slut punkt** (ux_host_stack_endpoint_transfer_abort) |
| ![Registrerings ikon för värd stack värd styrenhet](./media/user-guide/usbx-events/image203.png)    | Värd **styrenhets register värd styrenhet** *(ux_host_stack_hcd_register)* |
| ![Ikon för att initiera värd stack](./media/user-guide/usbx-events/image204.png)    | **Värd stack initiering** *(ux_host_stack_initialize)* |
| ![Hämta ikon för värd stackens gränssnitts slut punkt](./media/user-guide/usbx-events/image205.png)    | **Hämtnings punkt för värd stack gränssnitt** *(ux_host_stack_interface_endpoint_get)* |
| ![Ikon för att skapa värd stack gränssnitts instans](./media/user-guide/usbx-events/image206.png)    | **Värd stack gränssnitts instans skapa** *(ux_host_stack_interface_instance_create)* |
| ![Borttagnings ikon för värd stackens gränssnitts instans](./media/user-guide/usbx-events/image207.png)    | **Borttagning av värd Stacks gränssnitts instans** *(ux_host_stack_interface_instance_delete)* |
| ![Ikon för värd stack gränssnitts uppsättning](./media/user-guide/usbx-events/image208.png)    | **Värd stack gränssnitts uppsättning** *(ux_host_stack_interface_set)* |
| ![Inställnings ikon för värd Stacks gränssnitt](./media/user-guide/usbx-events/image209.png)    | **Välj värd stack gränssnitts inställning** *(ux_host_stack_interface_setting_select)* |
| ![Värd stack ny ikon för att skapa konfiguration](./media/user-guide/usbx-events/image210.png)    | **Värd stack ny konfiguration skapa** *(ux_host_stack_new_configuration_create)* |
| ![Ikon för att skapa en ny enhet för värd stack](./media/user-guide/usbx-events/image211.png)    | **Värd stack ny enhet skapa** *(ux_host_stack_new_device_create)* |
| ![Skapa ikon för värd stack för ny slut punkt](./media/user-guide/usbx-events/image212.png)    | **Skapa en ny slut punkt för värd stacken** *(ux_host_stack_new_endpoint_create)* |
| ![Ikon för ändrings process för värd stackens rot nav](./media/user-guide/usbx-events/image213.png)    | **Ändrings process för stacken i värd stacken** *(ux_host_stack_rh_change_process)* |
| ![Ikon för extrahering av värd stack för rot nav](./media/user-guide/usbx-events/image214.png)    | **Värd stack för rot nav för enhet** *(ux_host_stack_rh_device_extraction)* |
| ![Ikon för värd stack för rot nav enhet](./media/user-guide/usbx-events/image215.png)    | **Värd stack rot nav för enhets infogning** *(ux_host_stack_rh_device_insertion)* |
| ![Ikon för värd stack överförings förfrågan](./media/user-guide/usbx-events/image216.png)    | **Begäran om värd-stack-överföring** *(ux_host_stack_transfer_request)* |
| ![Avbryt ikon för begäran om värd stack överföring](./media/user-guide/usbx-events/image217.png)    | **Avbrott i värd stack överförings förfrågan** *(ux_host_stack_transfer_request_abort)* |
| ![Fel ikon för U S B X](./media/user-guide/usbx-events/image218.png)    | **USBX-fel** *(ux_error)* |

## <a name="event-descriptions"></a>Händelse beskrivningar

Följande sidor beskriver USBX spårnings händelser.

### <a name="device-class-cdc-activate"></a>Enhets klass CDC-aktivering 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Ikonen** ![ Enhets klass C D C Aktivera ikon](./media/user-guide/usbx-events/image1.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass CDC-aktiverings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-cdc-deactivate"></a>CDC-inaktive ring av enhets klass 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Ikonen** ![ Enhets klass C D C inaktivera ikon](./media/user-guide/usbx-events/image2.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass CDC-inaktive rad.

Informations fält 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-cdc-read"></a>Läsning av enhets klass CDC 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Ikonen** ![ Enhets klass C D C Läs ikon](./media/user-guide/usbx-events/image3.png)

**Beskrivning**

Den här händelsen representerar läsnings händelsen för en USBX-enhets klass CDC.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="device-class-cdc-write"></a>Enhets klass CDC-skrivning 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Ikonen** ![ Enhets klass C D s Skriv ikon](./media/user-guide/usbx-events/image4.png)

**Beskrivning**

Den här händelsen representerar en skrivnings händelse för USBX-enhetens klass CDC.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="device-class-dpump-activate"></a>Aktivering av enhets klass Dpump 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Ikonen** ![ Dpump Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image5.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Dpump aktivera händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-dpump-deactivate"></a>Inaktive ring av enhets klass Dpump 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Ikonen** ![ Ikon för Dpump för enhets klass](./media/user-guide/usbx-events/image6.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Dpump-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-dpump-read"></a>Läsning av enhets klassens Dpump 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Ikonen** ![ Läs ikon för enhets klassens Dpump](./media/user-guide/usbx-events/image7.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Dpump Read event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: buffert.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="device-class-dpump-write"></a>Skrivning av enhets klass Dpump 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Ikonen** ![ Dpump Skriv ikon för enhets klass](./media/user-guide/usbx-events/image8.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Dpump Skriv händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="device-class-hid-activate"></a>HID-aktivering för enhets klass 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Ikonen** ![ Ikon för HID-aktivering i enhets klass](./media/user-guide/usbx-events/image9.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass HID Activate-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-hid-deactivate"></a>HID-inaktive ring av enhets klass 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Ikonen** ![ Ikon för HID-inaktivera enhets klass](./media/user-guide/usbx-events/image10.png)

**Beskrivning**

Den här händelsen representerar en händelse för HID-inaktive ring av USBX enhets klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-hid-descriptor-send"></a>Skicka HID-beskrivning för enhets klass 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Ikonen** ![ Ikon för att skicka HID-beskrivning för enhets klass](./media/user-guide/usbx-events/image11.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass som en händelse för att skicka HID-beskrivning.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: beskrivnings typ.
- Informations fält 3: begär index.
- Info fält 4: används inte.

### <a name="device-class-hid-event-get"></a>Hämta HID-händelse för enhets klass 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Ikonen** ![ Ikonen Hämta ikon för enhets klassens HID-händelse](./media/user-guide/usbx-events/image12.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass HID Event get event.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-hid-event-set"></a>HID-händelse uppsättning för enhets klass 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Ikonen** ![ Ikon uppsättnings ikon för HID-händelseloggen i enhets klass](./media/user-guide/usbx-events/image13.png)

**Beskrivning**

Den här händelsen representerar en HID-USBX för enhets klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-hid-report-get"></a>Hämta HID-rapport för enhets klass 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Ikonen** ![ Ikonen Hämta ikon för enhets klassens HID-rapport](./media/user-guide/usbx-events/image14.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass HID Report get event.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: beskrivnings typ.
- Informations fält 3: begär index.
- Info fält 4: används inte.

### <a name="device-class-hid-report-set"></a>HID-rapport uppsättning för enhets klass 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Ikonen** ![ Ikon för HID-rapport för enhets klass](./media/user-guide/usbx-events/image15.png)

**Beskrivning**

Den här händelsen representerar en händelse för en HID-rapport för USBX-enhets klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: beskrivnings typ.
- Informations fält 3: begär index.
- Info fält 4: används inte.

### <a name="device-class-pima-activate"></a>Aktivering av enhets klass Pima

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Ikonen** ![ Pima Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image16.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima aktivera händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-deactivate"></a>Inaktive ring av enhets klass Pima 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Ikonen** ![ Ikon för Pima för enhets klass](./media/user-guide/usbx-events/image17.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-device-info-send"></a>Skicka enhets information i enhets klass Pima 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Ikonen** ![ Enhets klass Pima enhets information skicka ikon](./media/user-guide/usbx-events/image18.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima skicka händelse för enhets information.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.

### <a name="device-class-pima-event-get"></a>Hämta Pima-händelse i enhets klass 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Ikonen** ![ Enhets klass Pima händelse Hämta ikon](./media/user-guide/usbx-events/image19.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima Event get event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: Pima-händelse.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-event-set"></a>Pima händelse uppsättning för enhets klass 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Ikonen** ![ Enhets klass Pima händelse uppsättnings ikon](./media/user-guide/usbx-events/image20.png)

**Beskrivning**

Den här händelsen representerar händelse uppsättnings händelsen för en USBX enhets klass Pima.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: Pima-händelse.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-object-add"></a>Enhets klass Pima objekt Lägg till 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Ikonen** ![ Enhets klass Pima objekt Lägg till ikon](./media/user-guide/usbx-events/image21.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt Lägg till händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-object-data-get"></a>Hämta Pima objekt data för enhets klass 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Ikonen** ![ Enhets klass Pima objekt data hämta ikon](./media/user-guide/usbx-events/image22.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt data hämta händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-object-data-send"></a>Skicka objekt data från enhets klass Pima 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Ikonen** ![ Ikon för att skicka Pima objekt data i enhets klass](./media/user-guide/usbx-events/image23.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt data sändnings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-object-delete"></a>Ta bort Pima objekt i enhets klass 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Ikonen** ![ Pima objekt borttagnings ikon för enhets klass](./media/user-guide/usbx-events/image24.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt Delete event.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-object-handles-send"></a>Skicka i enhets klassens Pima-objekt 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Ikonen** ![ Skicka ikon för Pima objekt i enhets klass](./media/user-guide/usbx-events/image25.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt som skickar händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: lagrings-ID.
- Info-fält 3: kod för objekt format.
- Info-fält 4: objekt Association.

### <a name="device-class-pima-object-info-get"></a>Hämta Pima objekt information för enhets klass 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikonen** ![ Enhets klass Pima objekt information Hämta ikon](./media/user-guide/usbx-events/image26.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt information get-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-object-info-send"></a>Skicka Pima objekt information i enhets klass 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikonen** ![ Skicka ikon för Pima objekt information i enhets klass](./media/user-guide/usbx-events/image27.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt information skicka händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-objects-number-send"></a>Skicka Pima objekt nummer i enhets klass 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Ikonen** ![ Enhets klass Pima objekt nummer skicka ikon](./media/user-guide/usbx-events/image28.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima objekt nummer skicka händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: lagrings-ID.
- Info-fält 3: kod för objekt format.
- Info-fält 4: objekt associeras.

### <a name="device-class-pima-partial-object-data-get"></a>Hämtning av partiella objekt data för enhets klass Pima

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Ikonen** ![ Enhets klass Pima del objekt data hämta ikon](./media/user-guide/usbx-events/image29.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima del objekt data hämta händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: offset begärd.
- Info fält 4: den begärda längden.

### <a name="device-class-pima-response-send"></a>Skicka svar för enhets klass Pima 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Ikonen** ![ Ikon för Pima svars sändning i enhets klass](./media/user-guide/usbx-events/image30.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima sändnings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: svars kod.
- Info-fält 3: nummer parameter.
- Info-fält 4: Pima-parameter 1.

### <a name="device-class-pima-storage-id-send"></a>Enhets klass Pima lagrings-ID skicka 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Ikonen** ![ Enhets klass Pima lagrings-ID skicka ikon](./media/user-guide/usbx-events/image31.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima Storage ID Send event.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-pima-storage-info-send"></a>Skicka Pima Storage-information i enhets klass 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Ikonen** ![ Enhets klass Pima Storage information skicka ikon](./media/user-guide/usbx-events/image32.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass Pima Storage information send event.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-activate"></a>Aktivering av enhets klass RNDIS 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Ikonen** ![ RNDIS Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image33.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS aktivera händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-deactivate"></a>Inaktive ring av enhets klass RNDIS 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Ikonen** ![ Ikon för RNDIS för enhets klass](./media/user-guide/usbx-events/image34.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-message-keep-alive"></a>Enhets klass RNDIS meddelande Keep Alive 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**Ikonen** ![ Enhets klass RNDIS meddelande ikonen Behåll Alive](./media/user-guide/usbx-events/image35.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS meddelande om att händelsen "Keep Alive".

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-message-query"></a>RNDIS meddelande fråga för enhets klass 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Ikonen** ![ RNDIS meddelande fråga i enhets klass](./media/user-guide/usbx-events/image36.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS meddelande händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: RNDIS OID.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-message-reset"></a>RNDIS meddelande återställning för enhets klass 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Ikonen** ![ Ikon för enhets klass RNDIS meddelande återställning](./media/user-guide/usbx-events/image37.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS Message rereset-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.

### <a name="device-class-rndis-message-set"></a>RNDIS meddelande uppsättning för enhets klass 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Ikonen** ![ Enhets klass RNDIS meddelande uppsättnings ikon](./media/user-guide/usbx-events/image38.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS meddelande uppsättnings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: RNDIS OID.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-packet-receive"></a>Mottagning av enhets klassens RNDIS-paket 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Ikonen** ![ Ikon för enhets klassens RNDIS-paket](./media/user-guide/usbx-events/image39.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS Packet Receive-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-rndis-packet-transmit"></a>Överföring av RNDIS-paket i enhets klass 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Ikonen** ![ Enhets klass RNDIS Packet sändnings ikon](./media/user-guide/usbx-events/image40.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass RNDIS Packet sändnings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-activate"></a>Aktivera enhets klass lagring 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Ikonen** ![ Aktiverings ikon för enhets klass lagring](./media/user-guide/usbx-events/image41.png)

**Beskrivning**

Den här händelsen representerar en händelse för aktivering av USBX enhets klass lagring.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-deactivate"></a>Inaktive ring av enhets klass lagring 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Ikonen** ![ Ikon för enhets klassens lagrings inaktive rad](./media/user-guide/usbx-events/image42.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagrings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-format"></a>Lagrings format för enhets klass 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Ikonen** ![ Ikon för lagrings format för enhets klass](./media/user-guide/usbx-events/image43.png)

**Beskrivning**

Den här händelsen representerar ett USBX för enhets klassens lagrings format.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-inquiry"></a>Förfrågan om enhets klass lagring 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Ikonen** ![ Ikon för enhets klass lagrings förfrågan](./media/user-guide/usbx-events/image44.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagrings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-mode-select"></a>Val av enhets klassens lagrings läge

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Ikonen** ![ Enhets klassens lagrings läge Välj ikon](./media/user-guide/usbx-events/image45.png)

**Beskrivning**

Den här händelsen representerar ett USBX enhets klass lagrings läge Välj händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-mode-sense"></a>Sense i enhets klassens lagrings läge 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Ikonen** ![ Ikon för lagrings läge i enhets klass](./media/user-guide/usbx-events/image46.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagrings läges händelse.

Informations fält 

- NFO-fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-prevent-allow-media-removal"></a>Enhets klass lagring förhindra borttagning av media 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Ikonen** ![ Enhets klass lagring förhindra att ikonen borttagning av media](./media/user-guide/usbx-events/image47.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagring förhindra händelsen borttagning av media.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-read"></a>Läsning av enhets klass lagring 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Ikonen** ![ Läs ikon för enhets klass lagring](./media/user-guide/usbx-events/image48.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagrings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: sektor.
- Info fält 4: numrerade sektorer.

### <a name="device-class-storage-read-capacity"></a>Läs kapacitet för enhets klass lagring 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Ikonen** ![ Enhets klass lagring Läs kapacitets ikon](./media/user-guide/usbx-events/image49.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagrings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-read-format-capacity"></a>Kapacitet för Läs format för enhets klass lagring 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Ikonen** ![ Kapacitets ikon för Läs format för enhets klass lagring](./media/user-guide/usbx-events/image50.png)

**Beskrivning**

Den här händelsen representerar en USBX för enhets klass lagrings kapacitet.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-read-toc"></a>Läs innehålls förteckning för enhets klass lagring 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Ikonen** ![ Enhets klass lagring läsa innehålls förtecknings ikon](./media/user-guide/usbx-events/image51.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagring läsa TOC-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-request-sense"></a>Sense-begäran för enhets klass 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Ikonen** ![ Ikon för enhets klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image52.png)

**Beskrivning**

Den här händelsen representerar en händelse för en USBX enhets klass lagrings förfrågan.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Info-fält 3: Sense-nyckel.
- Info fält 4: kod.

### <a name="device-class-storage-start-stop"></a>Start stopp för enhets klass lagring 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Ikonen** ![ Start stopps ikon för enhets klass lagring](./media/user-guide/usbx-events/image53.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagrings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-test-ready"></a>Lagrings test för enhets klass klar 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Ikonen** ![ Ikon för lagrings test för enhets klass](./media/user-guide/usbx-events/image54.png)

**Beskrivning**

Den här händelsen representerar en USBX för enhets klass lagrings test.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-verify"></a>Verifiera lagring av enhets klass 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Ikonen** ![ Enhets klass lagring verifiera ikon](./media/user-guide/usbx-events/image55.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets klass lagring verifiera händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-class-storage-write"></a>Skrivning av enhets klass lagring 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Ikonen** ![ Skriv ikon för enhets klass lagring](./media/user-guide/usbx-events/image56.png)

**Beskrivning**

Den här händelsen representerar en Skriv händelse för lagring av USBX enhets klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: LUN.
- Informations fält 3: sektor.
- Info fält 4: numrerade sektorer.

### <a name="device-stack-alternate-setting-get"></a>Alternativ inställning för enhets stack Hämta 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Ikonen** ![ Alternativ inställnings ikon för enhets stack](./media/user-guide/usbx-events/image57.png)

**Beskrivning**

Den här händelsen representerar en alternativ inställnings händelse för USBX Device stack.

**Informations fält**

- Info-fält 1: gränssnitts värde.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-alternate-setting-set"></a>Alternativ inställnings uppsättning för enhets stack 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Ikonen** ![ Ikon för alternativ inställnings uppsättning för enhets stack](./media/user-guide/usbx-events/image58.png)

**Beskrivning**

Den här händelsen representerar en händelse för alternativ inställnings uppsättning för USBX-enhets stack.

**Informations fält**
- Info-fält 1: gränssnitts värde.
- Info-fält 2: värde för alternativ inställning.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-class-register"></a>Enhets Stack klass register 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Ikonen** ![ Enhets Stack klass register ikon](./media/user-guide/usbx-events/image59.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets Stack klass register händelse.

**Informations fält**

- Informations fält 1: klass namn.
- Informations fält 2: gränssnitts nummer.
- Info-fält 3: parameter.
- Info fält 4: används inte.

### <a name="device-stack-clear-feature"></a>Rensnings funktion för enhets stack 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Ikonen** ![ Enhets stack rensa funktions ikon](./media/user-guide/usbx-events/image60.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets stack rensa funktions händelse.

**Informations fält**

- Informations fält 1: typ av begäran.
- Info-fält 2: värde för begäran. Informations fält 3: begär index.
- Info fält 4: används inte.

### <a name="device-stack-configuration-get"></a>Hämta enhets stack konfiguration 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Ikonen** ![ Hämta ikon för enhets stack konfiguration](./media/user-guide/usbx-events/image61.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets stack konfiguration Hämta händelse.

**Informations fält** 

- Informations fält 1: konfigurations värde.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-configuration-set"></a>Konfigurations uppsättning för enhets stack 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Ikonen** ![ Ikon för enhets stack konfigurations uppsättning](./media/user-guide/usbx-events/image62.png)

**Beskrivning**

Den här händelsen representerar en händelse för konfigurations uppsättning för USBX Device stack-konfiguration.

**Informations fält** 

- Informations fält 1: konfigurations värde.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-connect"></a>Enhets stack anslutning 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Ikonen** ![ Enhets stackens anslutnings ikon](./media/user-guide/usbx-events/image63.png)

**Beskrivning**

Den här händelsen representerar en USBX för enhets stack beskrivning.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-descriptor-send"></a>Skicka enhets Stacks Beskrivning 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Ikonen** ![ Ikon för att skicka enhets stack Beskrivning](./media/user-guide/usbx-events/image64.png)

**Beskrivning**

Den här händelsen representerar en USBX för enhets stack beskrivning.

**Informations fält**

- Informations fält 1: beskrivnings typ.
- Informations fält 2: begär index.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-disconnect"></a>Enhets stack från koppling 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Ikonen** ![ Ikon för enhets stack från koppling](./media/user-guide/usbx-events/image65.png)

**Beskrivning**

Den här händelsen representerar en händelse för USBX enhets stack från koppling.

**Informations fält**

- Info fält 1: enhet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-endpoint-stall"></a>Enhets stackens slut punkt bås 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Ikonen** ![ Ikon för enhets stackens slut punkts bås](./media/user-guide/usbx-events/image66.png)

**Beskrivning**

Den här händelsen representerar en händelse för USBX Device stack Endpoint bås.

**Informations fält** 

- Informations fält 1: slut punkt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-get-status"></a>Hämta status för enhets stack 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Ikonen** ![ Enhets stack Hämta status ikon](./media/user-guide/usbx-events/image67.png)

**Beskrivning**

Den här händelsen representerar en USBX enhets stack Hämta status händelse.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-host-wakeup"></a>Aktivering av enhets stack värd 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Ikonen** ![ Aktiverings ikon för värd för enhets stack](./media/user-guide/usbx-events/image68.png)

**Beskrivning**

Den här händelsen representerar en aktiverings händelse för USBX Device stack-värden.

**Informations fält** 

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-initialize"></a>Initiera enhets stack 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Ikonen** ![ Ikon för enhets stack initierare](./media/user-guide/usbx-events/image69.png)

**Beskrivning**

Den här händelsen representerar en händelse för initiering av USBX enhets stack.

**Informations fält** 

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-interface-delete"></a>Ta bort enhets Stacks gränssnitt 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Ikonen** ![ Borttagnings ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image70.png)

**Beskrivning**

Den här händelsen representerar en händelse för borttagning av USBX Device stack-gränssnitt.

**Informations fält**

- Informations fält 1: gränssnitt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-interface-get"></a>Hämta enhets stack gränssnitt 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Ikonen** ![ Hämta ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image71.png)

**Beskrivning**

Den här händelsen representerar en händelse för hämtning av USBX Device stack-gränssnitt.

**Informations fält** 

- Info-fält 1: gränssnitts värde.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-interface-set"></a>Enhets stack gränssnitts uppsättning 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Ikonen** ![ Ikon för enhets stackens gränssnitts uppsättning](./media/user-guide/usbx-events/image72.png)

**Beskrivning**

Den här händelsen representerar en händelse för en USBX enhets stack gränssnitts uppsättning.

**Informations fält** 

- Informations fält 1: värde för begäran. Informations fält 2: begär index.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-set-feature"></a>Enhets stack uppsättnings funktion 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Ikonen** ![ Funktions ikon för enhets stack uppsättning](./media/user-guide/usbx-events/image73.png)

**Beskrivning**

Den här händelsen representerar en funktions händelse för en USBX enhets stack uppsättning.

**Informations fält** 

- Informations fält 1: värde för begäran. Informations fält 2: begär index.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-transfer-abort"></a>Avbryt enhets stack överföring 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Ikonen** ![ Avbrotts ikon för enhets stack överföring](./media/user-guide/usbx-events/image74.png)

**Beskrivning**

Den här händelsen representerar en avbrotts händelse för USBX Device stack-överföring.

**Informations fält** 

- Informations fält 1: överförings förfrågan.
- Info fält 2: slut för ande kod.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-transfer-all-request-abort"></a>Enhets stack överför alla begäran om att avbryta begäran 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Ikonen** ![ Ikon för enhets stacken överför alla begär Anden](./media/user-guide/usbx-events/image75.png)

**Beskrivning**

Den här händelsen representerar en USBX Device stack-överföring alla begär Anden om att avbryta begäran.

**Informations fält** 

- Informations fält 1: slut punkt.
- Info fält 2: slut för ande kod.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="device-stack-transfer-request"></a>Begäran om enhets stack överföring 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Ikonen** ![ Ikon för begäran om enhets stack-överföring](./media/user-guide/usbx-events/image76.png)

**Beskrivning**

Den här händelsen representerar en begäran om USBX enhets stack-överföring.

**Informations fält**

- Informations fält 1: överförings förfrågan.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-asix-activate"></a>Aktivering av värd klass Asix 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Ikonen** ![ Asix Aktivera ikon för värd klass](./media/user-guide/usbx-events/image77.png)

**Beskrivning**

Den här händelsen representerar en USBX-Asix för värd klass.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-asix-deactivate"></a>Asix inaktive ring av värd klass 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Ikonen** ![ Asix-ikon för värd klass](./media/user-guide/usbx-events/image78.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Asix-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-asix-interrupt-notification"></a>Avbrotts meddelande för värd klass Asix 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Ikonen** ![ Asix för värd klassens avbrotts meddelande](./media/user-guide/usbx-events/image79.png)

**Beskrivning**

Den här händelsen representerar en USBX Asix-avbrotts meddelande händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-asix-read"></a>Läsning av värd klass Asix 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Ikonen** ![ Läs ikon för värd klassen Asix](./media/user-guide/usbx-events/image80.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Asix Read event.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-asix-write"></a>Skrivning av värd klass Asix 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Ikonen** ![ Asix Skriv ikon för värd klass](./media/user-guide/usbx-events/image81.png)

**Beskrivning**

Den här händelsen representerar en USBX Asix Skriv händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-audio-activate"></a>Aktivera ljud för värd klass 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Ikonen** ![ Ikon för ljud aktivering i värd klass](./media/user-guide/usbx-events/image82.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass ljud.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-audio-control-value-get"></a>Hämta ljud kontroll värde för värd klass 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Ikonen** ![ Ikonen Hämta ljud kontroll värde i värd klass](./media/user-guide/usbx-events/image83.png)

**Beskrivning**

Den här händelsen representerar en händelse för ett ljud kontroll värde i USBX Host-klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-audio-control-value-set"></a>Värde uppsättning för ljud kontroll i värd klass 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Ikonen** ![ Ikon för ljud kontroll värde för värd klass](./media/user-guide/usbx-events/image84.png)

**Beskrivning**

Den här händelsen representerar en intern NetX I/O-drivrutin som Uppskjut bearbetnings händelsen.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: ljud kontroll.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-audio-deactivate"></a>Ljud inaktive ring av värd klass 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Ikonen** ![ Ikon för ljud inaktive ring av värd klass](./media/user-guide/usbx-events/image85.png)

**Beskrivning**

Den här händelsen representerar en ljud inaktive rings händelse för USBX värd klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-audio-read"></a>Ljud läsning av värd klass 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Ikonen** ![ Ljud läsnings ikon för värd klass](./media/user-guide/usbx-events/image86.png)

**Beskrivning**

Den här händelsen representerar en USBX för ljud läsnings händelse för värd klass.

- Informations fält 
- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-audio-streaming-sampling-get"></a>Ljud uppspelning av värd klass, samplings hämtning 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Ikonen** ![ Exempel på hämtnings ikon för värd klassens ljud strömning](./media/user-guide/usbx-events/image87.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass för ljud uppspelning.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-audio-streaming-sampling-set"></a>Samplings uppsättning för värd klassens ljud strömning 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Ikonen** ![ Ikon för samplings uppsättning för värd klassens ljud strömning](./media/user-guide/usbx-events/image88.png)

**Beskrivning**

Den här händelsen representerar en insamlings händelse för ljud strömning i USBX Host Class.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: ljud sampling.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-audio-write"></a>Ljud skrivning för värd klass 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Ikonen** ![ Ljud Skriv ikon för värd klass](./media/user-guide/usbx-events/image89.png)

**Beskrivning**

Den här händelsen representerar en ljud skrivnings händelse för en USBX värd klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-activate"></a>Värd klass CDC-ACM aktivera 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Ikonen** ![ Värd klass C D C A C M Aktivera ikon](./media/user-guide/usbx-events/image90.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM aktivera händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-deactivate"></a>Värd klass CDC ACM-inaktive ring 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Ikonen** ![ Värd klass C D C A C M inaktivera ikon](./media/user-guide/usbx-events/image91.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM-händelsen.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Värd klass CDC ACM IOCTL abort i pipe 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Ikonen** ![ Värd klass C D C A C M I O C T L avbryter i pipe-ikonen](./media/user-guide/usbx-events/image92.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL abort i pipe-händelse.

Informations fält 

- Informations fält 1: klass instans.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Värd klass CDC ACM IOCTL avbryter pipe 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Ikon** ! [[Värd klass C D c A c M I O c T L ta bort pipe-ikon](./media/user-guide/usbx-events/image93.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL avbryter pipe-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Värd klass CDC ACM IOCTL Hämta enhets status 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Ikonen** ![ Värd klass C D C A C M I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image94.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL get enhets status händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: enhets status.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Värd klass CDC ACM IOCTL get line-kodning 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Ikonen** ![ Värd klass C D C A C M I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image95.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL get line kodnings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Återanrop för värd klass CDC ACM IOCTL-meddelande

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Ikonen** ![ Värd klass C D C A C M I O C T L ikon för återanrop i meddelande](./media/user-guide/usbx-events/image96.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass CDC ACM IOCTL-meddelande.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Värd klass CDC ACM IOCTL skicka rast 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Ikonen** ![ Värd klass C D C A C M I O C T L-ikonen skicka rast](./media/user-guide/usbx-events/image97.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL Send Break event.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Värd klass CDC ACM IOCTL set line-kodning 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Ikonen** ![ Värd klass C D C A C M I O C T L v Ange ikon ikon för linje kodning ](./media/user-guide/usbx-events/image97.png) ] (./media/user-guide/usbx-events/image98.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass CDC ACM IOCTL som anger linje kodning.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Värd klass CDC ACM IOCTL ange linje status 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Ikonen** ![ Värd klass C D C A C M I O C T L ikon för ange linje tillstånd](./media/user-guide/usbx-events/image99.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass CDC ACM IOCTL set line State event.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-read"></a>Värd klass CDC ACM Read 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Ikonen** ![ Värd klass C D A C M Läs ikon](./media/user-guide/usbx-events/image100.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass CDC ACM Read event.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-reception-start"></a>Start av värd klassens CDC-ACM 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Ikonen** ![ Start ikon för värd klass C D A C M](./media/user-guide/usbx-events/image101.png)

**Beskrivning**

Den här händelsen representerar start händelsen för en USBX-värd klass CDC-ACM.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-reception-stop"></a>Stopp för värd klass CDC-ACM 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Ikonen** ![ Svars ikon för värd klass C D A C M](./media/user-guide/usbx-events/image102.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass CDC ACM.

**Informations fält**

- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-cdc-acm-write"></a>Värd klass CDC ACM-skrivning 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Ikonen** ![ Värd klass C D A C M Skriv ikon](./media/user-guide/usbx-events/image103.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass CDC ACM Write event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-dpump-activate"></a>Aktivering av värd klass Dpump 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Ikonen** ![ Dpump Aktivera ikon för värd klass](./media/user-guide/usbx-events/image104.png)

**Beskrivning**

Den här händelsen representerar en USBX-Dpump aktiverings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-dpump-deactivate"></a>Dpump inaktive ring av värd klass 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Ikonen** ![ Dpump-ikon för värd klass](./media/user-guide/usbx-events/image105.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Dpump-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-dpump-read"></a>Läsning av värd klass Dpump 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Ikonen** ![ Läs ikon för värd klassen Dpump](./media/user-guide/usbx-events/image106.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Dpump Read event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-dpump-write"></a>Skrivning av värd klass Dpump 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Ikonen** ![ Dpump Skriv ikon för värd klass](./media/user-guide/usbx-events/image107.png)

**Beskrivning**

Den här händelsen representerar en USBX Dpump Skriv händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-hid-activate"></a>HID-aktivering för värd klass 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Ikonen** ![ Ikon för HID-aktivering i värd klass](./media/user-guide/usbx-events/image108.png)

**Beskrivning**

Den här händelsen representerar en HID-USBX för värd klass.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-client-register"></a>HID-klient register för värd klass 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Ikonen** ![ Register ikon för HID-klient för värd klass](./media/user-guide/usbx-events/image109.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för HID-klient för värd klass.

**Informations fält** 

- Informations fält 1: HID-klientcertifikat.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-deactivate"></a>HID-inaktive ring av värd klass 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Ikonen** ![ Ikon för HID-inaktivera värd klass](./media/user-guide/usbx-events/image110.png)

**Beskrivning**

Den här händelsen representerar en händelse för HID-inaktive ring av USBX värd klasser.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-idle-get"></a>HID-inaktivitet i värd klass 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Ikonen** ![ Ikon för HID-inaktivitet i värd klass](./media/user-guide/usbx-events/image111.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass HID inaktiv get-händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-idle-set"></a>HID inaktive rad värd klass 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Ikonen** ![ Ikon för HID inaktive rad värd klass](./media/user-guide/usbx-events/image112.png)

**Beskrivning**

Den här händelsen representerar en händelse för HID inaktive rad USBX-värd klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-keyboard-activate"></a>Aktivera HID-tangentbord för värd klass 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Ikonen** ![ Ikon för HID-tangentbordet för värd klass](./media/user-guide/usbx-events/image113.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass HID tangent bord aktivera händelse.

**Informations fält**
<p>Informations fält 1: klass instans.
<p>Info-fält 2: HID-klient instans.
<p>Informations fält 3: används inte.
<p>Info fält 4: används inte.

### <a name="host-class-hid-keyboard-deactivate"></a>HID-tangent bords inaktive ring för värd klass 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Ikonen** ![ Ikonen värd klass HID tangent bords inaktive ring](./media/user-guide/usbx-events/image114.png)

**Beskrivning**

Den här händelsen representerar en händelse för HID-tangentbordet för USBX-värd klass.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: HID-klient instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-mouse-activate"></a>Aktivera HID-mus för värd klass 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Ikonen** ![ Aktivera ikon för HID-mus i värd klass](./media/user-guide/usbx-events/image115.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass HID-mus aktivera händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: HID-klient instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-mouse-deactivate"></a>Inaktive ring av värd klass HID-mus 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Ikonen** ![ Värd klass HID-mus inaktivera ikon](./media/user-guide/usbx-events/image116.png)

**Beskrivning**

- Den här händelsen representerar en USBX-värd klass HID-mus.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: HID-klient instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-remote-control-activate"></a>Aktivera HID-fjärrstyrning av värd klass 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Ikonen** ![ Ikonen aktivera HID-fjärrstyrning i värd klass](./media/user-guide/usbx-events/image117.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass HID-fjärrstyrning.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: HID-klient instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-remote-control-deactivate"></a>HID-fjärrstyrning inaktive ras för värd klass 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Ikonen** ![ Ikon för HID-fjärrstyrning av värd klass](./media/user-guide/usbx-events/image118.png)

**Beskrivning**

Den här händelsen representerar en USBX-värd klass HID-fjärrstyrning.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: HID-klient instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-report-get"></a>Hämta HID-rapport för värd klass 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Ikonen** ![ Ikon för Hämta värd klass HID-rapport](./media/user-guide/usbx-events/image119.png)

**Beskrivning**

Den här händelsen representerar en HID-rapport för USBX-värd klass.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: klient rapport.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hid-report-set"></a>HID-rapport uppsättning för värd klass 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Ikonen** ![ Ikon för HID-rapport för värd klass](./media/user-guide/usbx-events/image120.png)

**Beskrivning** Den här händelsen representerar en HID-rapport uppsättning för USBX-värd klass.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: klient rapport.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hub-activate"></a>Aktivera värd klass hubb 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Ikonen** ![ Aktivera ikon för värd klassens hubb](./media/user-guide/usbx-events/image121.png)

**Beskrivning**

Den här händelsen representerar en aktiverings händelse för USBX Host Class Hub.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hub-change-detect"></a>Identifiera ändring av värd klassens hubb 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Ikonen** ![ Identifiera ikon för värd klassens hubb ändring](./media/user-guide/usbx-events/image122.png)

**Beskrivning**

Den här händelsen representerar en händelse för att identifiera en USBX för värd klass ändringar.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hub-deactivate"></a>Inaktive ring av värd Klasss hubb 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**Ikonen** ![ Ikonen inaktivera ikon för värd klassens hubb](./media/user-guide/usbx-events/image123.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klassens hubb.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-hub-port-change-connection-process"></a>Anslutnings processen för värd klassens hubb port ändring 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Ikonen** ![ Ikon för att ändra anslutnings process för värd klassens hubb port](./media/user-guide/usbx-events/image124.png)

**Beskrivning**

Den här händelsen representerar en USBX anslutnings process händelse för värd klassens hubb.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: port.
- Info-fält 3: port status.
- Info fält 4: används inte.

### <a name="host-class-hub-port-change-enable-process"></a>Aktiverings processen för värd klassens Hubbs port ändring 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Ikonen** ![ Aktivera process ikon för värd klassens hubb port ändring](./media/user-guide/usbx-events/image125.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd Klasss Hub-port ändra Aktivera process händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: port.
- Info-fält 3: port status.
- Info fält 4: används inte.

### <a name="host-class-hub-port-change-over-current-process"></a>Port ändring i värd klassens hubb över den aktuella processen 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Ikonen** ![ Port ändring över ikon för värd Klasss hubb över den aktuella process ikonen](./media/user-guide/usbx-events/image126.png)

**Beskrivning**

Den här händelsen representerar att allokera ett paket via nx_packet_allocate.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: port.
- Info-fält 3: port status.
- Info fält 4: används inte.

### <a name="host-class-hub-port-change-reset-process"></a>Återställnings process för port ändring av värd klass 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Ikonen** ![ Ikon för ändrings process för värd klassens Hubbs port](./media/user-guide/usbx-events/image127.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass för värde ändrings återställning.

**Informations fält**

- Informations fält 1: hubb. Info fält 2: port.
- Info-fält 3: port status.
- Info fält 4: används inte.

### <a name="host-class-hub-port-change-suspend-process"></a>Inaktive ring av värd klassens hubb port ändring 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Ikonen** ![ Ikon för att inaktivera process klassens hubb port ändring](./media/user-guide/usbx-events/image128.png)

**Beskrivning**

Den här händelsen representerar en inaktive ring av en USBX för värd Klasss port ändring.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: port.
- Info-fält 3: port status.
- Info fält 4: används inte.

### <a name="host-class-pima-activate"></a>Aktivering av värd klass Pima 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Ikonen** ![ Pima Aktivera ikon för värd klass](./media/user-guide/usbx-events/image129.png)

**Beskrivning**

Den här händelsen representerar en USBX-Pima aktiverings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-deactivate"></a>Pima inaktive ring av värd klass 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Ikonen** ![ Pima-ikon för värd klass](./media/user-guide/usbx-events/image130.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Pima-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-device-info-get"></a>Hämta Pima enhets information för värd klass 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Ikonen** ![ Hämta ikon för värd klassens Pima enhets information](./media/user-guide/usbx-events/image131.png)

**Beskrivning**

Den här händelsen representerar en USBX Pima Device information get-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: Pima-enhet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-device-reset"></a>Återställning av värd klass Pima enhet 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Ikonen** ![ Enhets återställnings ikon för värd klass Pima](./media/user-guide/usbx-events/image132.png)

**Beskrivning**

Den här händelsen representerar en USBX Pima Device rereset-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-notification"></a>Pima-meddelande för värd klass 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Ikonen** ![ Meddelande ikon för värd klass Pima](./media/user-guide/usbx-events/image133.png)

**Beskrivning**

Den här händelsen representerar en USBX-meddelande händelse för värd klass Pima.

**Informations fält**

- Informations fält 1: klass instans. Info fält 2: händelse kod.
- Info-fält 3: transaktions-ID.
- Info fält 4: Parameter1.

### <a name="host-class-pima-number-objects-get"></a>Hämta Pima nummer objekt för värd klass 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Ikonen** ![ Ikon för Pima för värd klassens antal objekt](./media/user-guide/usbx-events/image134.png)

**Beskrivning**

Den här händelsen representerar en händelse för en USBX-värd klass Pima Number Objects.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-object-close"></a>Pima objekt stängning i värd klass 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Ikonen** ![ Ikonen Stäng Pima objekt i värd klass](./media/user-guide/usbx-events/image135.png)

**Beskrivning**

Den här händelsen representerar händelsen stängning av USBX Pima objekt.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-object-copy"></a>Pima objekt kopia av värd klass 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Ikonen** ![ Objekt kopierings ikon för värd klass Pima](./media/user-guide/usbx-events/image136.png)

**Beskrivning**

Den här händelsen representerar en USBX Pima objekt kopierings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-object-delete"></a>Ta bort värd klass Pima objekt 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Ikonen** ![ Pima objekt borttagnings ikon för värd klass](./media/user-guide/usbx-events/image137.png)

**Beskrivning**

Den här händelsen representerar en USBX Pima objekt borttagnings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-object-get"></a>Hämta Pima-objekt för värd klass 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Ikonen** ![ Pima objekt Hämta ikon för värd klass](./media/user-guide/usbx-events/image138.png)

**Beskrivning**

Den här händelsen representerar att hämta RARP-information via nx_rarp_info_get.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Info-fält 3: objekt.
- Info fält 4: används inte.

### <a name="host-class-pima-object-info-get"></a>Hämta Pima objekt information för värd klass 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Ikonen** ![ Hämta ikon för värd klassens Pima objekt information](./media/user-guide/usbx-events/image139.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass Pima objekt information.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Info-fält 3: objekt.
- Info fält 4: används inte.

### <a name="host-class-pima-object-info-send"></a>Skicka Pima objekt information i värd klass 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Ikonen** ![ Skicka ikon för Pima objekt information i värd klass](./media/user-guide/usbx-events/image140.png)

**Beskrivning**

Den här händelsen representerar sändnings händelsen för en USBX-Pima objekt information.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-object-move"></a>Flytt av Pima objekt i värd klass 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikonen** ![ Ikon för flytt av Pima objekt i värd klass](./media/user-guide/usbx-events/image141.png)

**Beskrivning**

Den här Event reprThis-händelsen representerar en USBX för värd klass Pima objekt.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Info-fält 3: objekt.
- Info fält 4: används inte.

### <a name="host-class-pima-object-send"></a>Skicka Pima objekt i värd klass 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikonen** ![ Ikon för att skicka Pima objekt i värd klass](./media/user-guide/usbx-events/image142.png)

**Beskrivning**

Den här händelsen representerar en USBX-Pima objekt sändnings händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt.
- Info-fält 3: objektets buffert.
- Info-fält 4: objekt längd.

### <a name="host-class-pima-object-transfer-abort"></a>Avbrytning av Pima objekt överföring i värd klass 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Ikonen** ![ Avbrotts ikon för Pima objekt överföring i värd klass](./media/user-guide/usbx-events/image143.png)

**Beskrivning**

Den här händelsen representerar en avbrotts händelse för USBX av värd klass Pima objekt överföring.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Info-fält 3: objekt.
- Info fält 4: används inte.

### <a name="host-class-pima-read"></a>Läsning av värd klass Pima 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Ikonen** ![ Läs ikon för värd klassen Pima](./media/user-guide/usbx-events/image144.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Pima Read event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: data längd.
- Info fält 4: används inte.

### <a name="host-class-pima-request-cancel"></a>Avbrotts förfrågan för värd klass Pima 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Ikonen** ![ Ikon för Pima-begäran i värd klass](./media/user-guide/usbx-events/image145.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Pima.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-session-close"></a>Pima-session för värd klass Stäng 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Ikonen** ![ Pima för värd klassens stängnings ikon](./media/user-guide/usbx-events/image146.png)

**Beskrivning**

Den här händelsen representerar en händelse för stängning av USBX Pima.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: Pima-sessionen.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-session-open"></a>Pima-session för värd klass öppen 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Ikonen** ![ Öppna Pima-ikonen för värd klassens session](./media/user-guide/usbx-events/image147.png)

**Beskrivning** Den här händelsen representerar en USBX Pima session Open event.

**Informations fält**

- Informations fält 1: klass instans.
- Info-fält 2: Pima-sessionen.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-storage-ids-get"></a>Pima lagrings-ID: n för värd klass 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Ikonen** ![ Pima lagrings-ID Hämta ikon för värd klass](./media/user-guide/usbx-events/image148.png)

**Beskrivning**

Den här händelsen representerar en händelse för USBX-Pima för värd klass lagrings-ID.

**Informations fält**

- Informations fält 1: klass instans.
- NFO-fält 2: matris för lagrings-ID.
- Informations fält 3: lagrings-ID-längd.
Info fält 4: används inte.

### <a name="host-class-pima-storage-info-get"></a>Hämta lagrings information för värd klass Pima 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Ikonen** ![ Pima Storage information get-ikon i värd klass](./media/user-guide/usbx-events/image149.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Pima Storage information get event.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: lagrings-ID.
- Informations fält 3: lagring.
- Info fält 4: används inte.

### <a name="host-class-pima-thumb-get"></a>Pima-skjutreglage för värd klass 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikonen** ![ Ikon för Pima för värd klass](./media/user-guide/usbx-events/image150.png)

**Beskrivning**

Den här händelsen representerar att ta emot en TCP-server-anslutning via nx_tcp_server_socket_unaccept.

**Informations fält** 

- Informations fält 1: klass instans.
- Info-fält 2: objekt referens.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-pima-write"></a>Skrivning av värd klass Pima 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikonen** ![ Pima Skriv ikon för värd klass](./media/user-guide/usbx-events/image151.png)

**Beskrivning**

Den här händelsen representerar en USBX Pima skrivning av värd klass.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: data längd.
- Info fält 4: används inte.

### <a name="host-class-printer-activate"></a>Aktivera värd klass skrivare 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Ikonen** ![ Aktivera ikon för värd klass skrivare](./media/user-guide/usbx-events/image152.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass skrivare.

**Informations fält**

- Informations fält 1: pekare till IP-instans.
- Info fält 2: pekare till Socket.
- Informations fält 3: typ av tjänst.
- Info fält 4: mottagnings fönster storlek.

### <a name="host-class-printer-deactivate"></a>Inaktivera värd klass skrivare 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Ikonen** ![ Ikon för att inaktivera värd klass skrivare](./media/user-guide/usbx-events/image153.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass skrivare.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-printer-name-get"></a>Hämta namn på värd klass skrivare 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Ikonen** ![ Hämta ikon för värd klassens skrivar namn](./media/user-guide/usbx-events/image154.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass skrivare namn.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-printer-read"></a>Läsning av värd klass skrivare 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Ikonen** ![ Läs ikon för värd klass skrivare](./media/user-guide/usbx-events/image155.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass skrivare.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-printer-soft-reset"></a>Mjuk återställning av värd klass skrivare 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Ikonen** ![ Ikon för mjuk återställning av värd klass skrivare](./media/user-guide/usbx-events/image156.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för mjuk återställning av värd klass skrivare.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-printer-status-get"></a>Hämta status för värd klass skrivare 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Ikonen** ![ Ikon för Hämta värd klass skrivar status](./media/user-guide/usbx-events/image157.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass skrivare status.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: skrivar status.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-printer-write"></a>Skrivning av värd klass skrivare 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Ikonen** ![ Skriv ikon för värd klass skrivare](./media/user-guide/usbx-events/image158.png)

**Beskrivning**

Den här händelsen representerar en USBX skrivning av värd klass.

**Informations fält** 

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-prolific-activate"></a>Aktivering av värd klass Prolific 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Ikonen** ![ Prolific Aktivera ikon för värd klass](./media/user-guide/usbx-events/image159.png)

**Beskrivning**

Den här händelsen representerar en USBX-Prolific aktiverings händelse.

**Informations fält** 

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-deactivate"></a>Prolific inaktive ring av värd klass 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Ikonen** ![ Prolific-ikon för värd klass](./media/user-guide/usbx-events/image160.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Prolific-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Värd klass Prolific IOCTL Avbryt i pipe 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Ikonen** ![ Prolific för värd klass I O C T L Avbryt i pipe-ikon](./media/user-guide/usbx-events/image161.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific IOCTL abort i pipe-händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Prolific för värd klass IOCTL avbryter pipe 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Ikonen** ![ Prolific för värd klass I O C T L ta bort pipe-ikon](./media/user-guide/usbx-events/image162.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific IOCTL-avbrott.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-get-device-status"></a>Värd klass Prolific IOCTL Hämta enhets status 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Ikonen** ![ Prolific för värd klass I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image163.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Prolific IOCTL get enhets status händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: enhets status.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Prolific IOCTL get line-kodning i värd klass 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Ikonen** ![ Prolific för värd klass I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image164.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific IOCTL get line.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-purge"></a>Prolific IOCTL-rensning för värd klass 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Ikonen** ![ Rensnings ikon för värd klassens Prolific IOCTL](./media/user-guide/usbx-events/image165.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific IOCTL.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-report-device"></a>Prolific IOCTL-rapport enhet för värd klass 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Ikonen** ![ Enhets ikon för värd klass Prolific I O d T L](./media/user-guide/usbx-events/image166.png)

**Beskrivning**

Den här händelsen representerar en status ändrings händelse för en USBX Prolific IOCTL-rapport enhet.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-send-break"></a>Prolific IOCTL för värd klass skicka rast 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Ikonen** ![ Prolific för värd klass I O C T L](./media/user-guide/usbx-events/image167.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific IOCTL Send Break.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Rad kodning för Prolific IOCTL för värd klass 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Ikonen** ![ Prolific för värd klass I O C T L ange rad kodnings ikon](./media/user-guide/usbx-events/image168.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific IOCTL-uppsättning.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-ioctl-set-line-state"></a>Prolific IOCTL ange linje status i värd klass 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Ikonen** ![ Ikon för värd klass Prolific I O C T L](./media/user-guide/usbx-events/image169.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Prolific IOCTL set line State event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: parameter.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-read"></a>Läsning av värd klass Prolific 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Ikonen** ![ Läs ikon för värd klassen Prolific](./media/user-guide/usbx-events/image170.png)

**Beskrivning**

Den här händelsen representerar en USBX värd klass Prolific Read event.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-prolific-reception-start"></a>Start av värd klass Prolific mottagning 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Ikonen** ![ Start ikon för Prolific mottagning i värd klass](./media/user-guide/usbx-events/image171.png)

**Beskrivning**

Den här händelsen representerar start händelsen för en USBX värd klass Prolific.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-reception-stop"></a>Sluta ta emot värd klass Prolific 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**Ikonen** ![ Stopp ikon för Prolific för värd klass](./media/user-guide/usbx-events/image172.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass Prolific mottagning.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-prolific-write"></a>Skrivning av värd klass Prolific 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Ikonen** ![ Prolific Skriv ikon för värd klass](./media/user-guide/usbx-events/image173.png)

**Beskrivning**

Den här händelsen representerar en USBX Prolific Skriv händelse.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: data pekare.
- Informations fält 3: begärd längd.
- Info fält 4: används inte.

### <a name="host-class-storage-activate"></a>Aktivera värd klass lagring 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Ikonen** ![ Aktivera ikon för värd klass lagring](./media/user-guide/usbx-events/image174.png)

**Beskrivning**

Den här händelsen representerar en händelse för aktivering av USBX värd klass lagring.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-deactivate"></a>Inaktive ring av värd klass lagring 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Ikonen** ![ Ikon för värd klass lagrings inaktive ring](./media/user-guide/usbx-events/image175.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass lagring.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-media-capacity-get"></a>Hämtning av värd klassens lagrings medium kapacitet 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Ikonen** ![ Ikon för Hämta värd klass lagrings medie kapacitet](./media/user-guide/usbx-events/image176.png)

**Beskrivning**

Den här händelsen representerar en händelse för USBX värd klass lagrings medie kapacitet.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-media-format-capacity-get"></a>Hämtnings kapacitet för värd klass lagrings medie format

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Ikonen** ![ Ikon för Hämta kapacitet för värd klass lagrings medie format](./media/user-guide/usbx-events/image177.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass lagring med medie format.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

#### <a name="host-class-storage-media-mount"></a>Montering av värd klass lagrings medium 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Ikonen** ![ Monterings ikon för värd klass lagrings medium](./media/user-guide/usbx-events/image178.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass lagrings medier.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: sektor.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-media-open"></a>Lagrings medier för värd klass öppen 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Ikonen** ![ Öppnings ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image179.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass lagrings medier.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: medium.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-media-read"></a>Läsning av värd klassens lagrings medium 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Ikonen** ![ Läs ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image180.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass lagrings medier.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: sektor start.
- Informations fält 3: antal sektorer.
- Info-fält 4: data pekare.

### <a name="host-class-storage-media-write"></a>Skrivning av värd klass lagrings medium 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Ikonen** ![ Skriv ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image181.png)

**Beskrivning**

Den här händelsen representerar en Skriv händelse för USBX Host Class Storage media.

**Informations fält**

- Informations fält 1: klass instans.
- Info fält 2: sektor start.
- Informations fält 3: antal sektorer.
- Info-fält 4: data pekare.

### <a name="host-class-storage-request-sense"></a>Sense-begäran om värd klass lagring 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Ikonen** ![ Ikon för värd klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image182.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för värd klass lagrings begär Anden.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-start-stop"></a>Start stopp för värd klass lagring 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Ikonen** ![ Start stopp ikon för värd klass lagring](./media/user-guide/usbx-events/image183.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd klass lagrings start.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: starta stopp signal.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-class-storage-unit-ready-test"></a>Redo test för värd klass lagrings enhet 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Ikonen** ![ Test ikon för värd klassens lagrings enhet](./media/user-guide/usbx-events/image184.png)

**Beskrivning**

Den här händelsen representerar test händelsen för USBX värd klass lagrings enhet.

**Informations fält**

- Informations fält 1: klass instans.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-class-instance-create"></a>Värd Stack klass instans skapa 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikonen** ![ Ikon för att skapa värd Stack klass instans](./media/user-guide/usbx-events/image185.png)

**Beskrivning**

Den här händelsen representerar en händelse för att skapa en USBX Host stack-instans.

**Informations fält**

- Informations fält 1: klass.
- Informations fält 2: klass instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-class-instance-destroy"></a>Förstöra värd Stack klass instans 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikonen** ![ Ikon för att förstöra värd Stack klass instans](./media/user-guide/usbx-events/image186.png)

**Beskrivning**

Den här händelsen representerar en händelse för förstöring av USBX Host stack-instanser.

**Informations fält**

- Informations fält 1: klass.
- Informations fält 2: klass instans.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-configuration-delete"></a>Ta bort värd stack konfiguration 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Ikonen** ![ Borttagnings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image187.png)

**Beskrivning**

Den här händelsen representerar en händelse för borttagning av en USBX Host stack-konfiguration.

**Informations fält**

- Informations fält 1: konfiguration.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-configuration-enumerate"></a>Uppräkning av värd stack konfiguration 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Ikonen** ![ Uppräknings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image188.png)

**Beskrivning**

Den här händelsen representerar en uppräknings händelse för USBX Host stack-konfiguration.

**Informations fält**

- Info fält 1: enhet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="stack-configuration-instance-create"></a>Skapa stack konfigurations instans 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Ikonen** ![ Skapa ikon för stack konfigurations instans](./media/user-guide/usbx-events/image189.png)

**Beskrivning**

Den här händelsen representerar en USBX för att skapa en händelse i värd stacken.

**Informations fält**

- Informations fält 1: konfiguration.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-configuration-instance-delete"></a>Borttagning av värd Stacks konfigurations instans 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Ikonen** ![ Borttagnings ikon för värd Stacks konfigurations instans](./media/user-guide/usbx-events/image190.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse som tar bort värd Stacks konfigurations instans.

**Informations fält**

- Informations fält 1: konfiguration.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-configuration-set"></a>Konfigurations uppsättning för värd stack 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Ikonen** ![ Ikon för konfigurations uppsättning för värd stack](./media/user-guide/usbx-events/image191.png)

**Beskrivning**

Den här händelsen representerar en händelse för konfigurations uppsättning för USBX värd stack.

**Informations fält**

- Informations fält 1: konfiguration.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-device-address-set"></a>Adress uppsättning för värd stack enhet 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Ikonen** ![ Ikon för värd stack enhetens adress uppsättning](./media/user-guide/usbx-events/image192.png)

**Beskrivning**

Den här händelsen representerar en händelse för en USBX-värd för stack enhet.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: enhets adress.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-device-configuration-get"></a>Hämta konfiguration av värd stack enhet 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Ikonen** ![ Hämta ikon för värd stack enhets konfiguration](./media/user-guide/usbx-events/image193.png)

**Beskrivning**

Den här händelsen representerar en USBX värd stack enhets konfiguration Hämta händelse.

**Informations fält**

- Info fält 1: enhet.
- NFO-fält 2: konfiguration.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-device-configuration-select"></a>Välj konfiguration av värd stack enhet 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Ikonen** ![ Konfiguration av värd stack enhets konfiguration Välj ikon](./media/user-guide/usbx-events/image194.png)

**Beskrivning**

Den här händelsen representerar en USBX för värd stack enhets konfiguration Välj händelse.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: konfiguration.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-device-descriptor-read"></a>Läsning av värd stack enhets Beskrivning 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Ikonen** ![ Läs ikon för värd stack enhets Beskrivning](./media/user-guide/usbx-events/image195.png)

**Beskrivning**

Den här händelsen representerar läsnings händelsen för en USBX värd Stacks enhets beskrivning.

**Informations fält**

- Info fält 1: enhet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-device-get"></a>Hämta värd stack enhet 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Ikonen** ![ Hämta ikon för värd stack enhet](./media/user-guide/usbx-events/image196.png)

**Beskrivning**

Den här händelsen representerar en händelse för att hämta en USBX värd stack enhet.

**Informations fält**

- Informations fält 1: enhets index.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-device-remove"></a>Ta bort värd stack enhet 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Ikonen** ![ Ikon för att ta bort värd stack enhet](./media/user-guide/usbx-events/image197.png)

**Beskrivning**

Den här händelsen representerar en händelse för att ta bort en USBX Host stack-enhet.

**Informations fält**

- Info-fält 1: HCD.
- Info-fält 2: överordnad.
- Info-fält 3: port index.
- Info fält 4: enhet.

### <a name="host-stack-device-resource-free"></a>Värd stack för enhets resurs kostnads fritt 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Ikonen** ![ Ikon för värd stack för enhets resurs](./media/user-guide/usbx-events/image198.png)

**Beskrivning**

Den här händelsen representerar en ledig händelse för en USBX värd stack för enhets resurser.

**Informations fält**

- Info fält 1: enhet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-endpoint-instance-create"></a>Skapa värd stack slut punkts instans skapa 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Ikonen** ![ Ikon för att skapa värd stack slut punkts instans](./media/user-guide/usbx-events/image199.png)

**Beskrivning**

Den här händelsen representerar en händelse för att skapa en USBX Host stack-slutpunkt.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-endpoint-instance-delete"></a>Ta bort värd stack slut punkts instans 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Ikonen** ![ Borttagnings ikon för värd stack slut punkts instans](./media/user-guide/usbx-events/image200.png)

**Beskrivning**

Den här händelsen representerar en händelse för borttagning av en USBX Host stack-slutpunkt.

**Informations fält**

- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-endpoint-reset"></a>Återställning av värd stack slut punkt 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Ikonen** ![ Ikon för återställning av värd stack slut punkt](./media/user-guide/usbx-events/image201.png)

**Beskrivning**

Den här händelsen representerar en händelse för återställning av USBX värd stack slut punkt.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-endpoint-transfer-abort"></a>Avbrytning av värd stack slut punkts överföring 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Ikonen** ![ Avbryt ikon för värd stack slut punkts överföring](./media/user-guide/usbx-events/image202.png)

**Beskrivning**

Den här händelsen representerar en avbrotts händelse för USBX värd stack slut punkts överföring.

**Informations fält**

- Informations fält 1: slut punkt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-host-controller-register"></a>Värd styrenhet registrera värd styrenhet 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Ikonen** ![ Registrerings ikon för värd stack värd styrenhet](./media/user-guide/usbx-events/image203.png)

**Beskrivning**

Den här händelsen representerar en register värd styrenhet för USBX värd.

**Informations fält**

- Info-fält 1: HCD-namn.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-initialize"></a>Värd stack initieras 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Ikonen** ![ Ikon för att initiera värd stack](./media/user-guide/usbx-events/image204.png)

**Beskrivning**

Den här händelsen representerar en händelse för att initiera en USBX-värd.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-interface-endpoint-get"></a>Hämtning av värd stack gränssnitt slut punkt 

#### <a name="interface_-tcp-retry-entry"></a>Interface_ TCP-återförsöksintervallet

**Ikonen** ![ Hämta ikon för värd stackens gränssnitts slut punkt](./media/user-guide/usbx-events/image205.png)

**Beskrivning**

Den här händelsen representerar en intern NetX-händelse för TCP-försök.

**Informations fält**

- Informations fält 1: gränssnitt.
- Info-fält 2: slut punkts index.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-interface-instance-create"></a>Skapa värd stack gränssnitts instans 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Ikonen** ![ Ikon för att skapa värd stack gränssnitts instans](./media/user-guide/usbx-events/image206.png)

**Beskrivning**

Den här händelsen representerar en USBX-händelse för en värd stack instans.

**Informations fält**

- Informations fält 1: gränssnitt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-interface-instance-delete"></a>Borttagning av värd Stacks gränssnitts instans 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Ikonen** ![ Borttagnings ikon för värd stackens gränssnitts instans](./media/user-guide/usbx-events/image207.png)

**Beskrivning**

Den här händelsen representerar en händelse för borttagning av en USBX Host stack Interface-instans.

**Informations fält**

- Informations fält 1: gränssnitt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-interface-set"></a>Värd stack gränssnitts uppsättning 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Ikonen** ![ Ikon för värd stack gränssnitts uppsättning](./media/user-guide/usbx-events/image208.png)

**Beskrivning**

Den här händelsen representerar en händelse för en gränssnitts uppsättning för USBX värd stack.

**Informations fält**

- Informations fält 1: gränssnitt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-interface-setting-select"></a>Inställning av värd stack gränssnitt Välj 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Ikonen** ![ Inställnings ikon för värd Stacks gränssnitt](./media/user-guide/usbx-events/image209.png)

**Beskrivning**

Den här händelsen representerar en gränssnitts inställning för en USBX. Välj händelse.

**Informations fält**

- Informations fält 1: gränssnitt.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-new-configuration-create"></a>Värd stack ny konfiguration skapa 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Ikonen** ![ Värd stack ny ikon för att skapa konfiguration](./media/user-guide/usbx-events/image210.png)

**Beskrivning**
 
Den här händelsen representerar en ny konfiguration för att skapa en USBX-värd.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: konfiguration.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-new-device-create"></a>Skapa värd stack ny enhet skapa 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Ikonen** ![ Ikon för att skapa en ny enhet för värd stack](./media/user-guide/usbx-events/image211.png)

**Beskrivning**
 
 Den här händelsen representerar en USBX-värd stack ny enhet skapa händelse.

**Informations fält**

- Info-fält 1: HCD.
- Informations fält 2: enhets ägare.
- Info-fält 3: port index.
- Info fält 4: enhet.

### <a name="host-stack-new-endpoint-create"></a>Skapa en ny slut punkt för värd stack 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Ikonen** ![ Skapa ikon för värd stack för ny slut punkt](./media/user-guide/usbx-events/image212.png)

**Beskrivning**
 
Den här händelsen representerar en ny slut punkt för att skapa en USBX-värd.

**Informations fält**

- Informations fält 1: gränssnitt.
- Info fält 2: slut punkt.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-root-hub-change-process"></a>Ändrings process för stacken för värd stackens rot nav 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Ikonen** ![ Ikon för ändrings process för värd stackens rot nav](./media/user-guide/usbx-events/image213.png)

**Beskrivning**
 
Den här händelsen representerar en ändrings process för USBX värd stackens rot nav.

**Informations fält**

- Info fält 1: port index.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-root-hub-device-extraction"></a>Värd stack för rot nav enhets extrahering 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Ikonen** ![ Ikon för extrahering av värd stack för rot nav](./media/user-guide/usbx-events/image214.png)

**Beskrivning**

Den här händelsen representerar en USBX värd stack för enhets stacken.

**Informations fält**

- Info-fält 1: HCD.
- Info fält 2: port index.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-root-hub-device-insertion"></a>Värd stack för rot Hubbs enhets infogning 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Ikonen** ![ Ikon för värd stack för rot nav enhet](./media/user-guide/usbx-events/image215.png)

**Beskrivning**

Den här händelsen representerar en USBX som anger att enheten ska infogas i värd stacken.

**Informations fält**

- Info-fält 1: HCD.
- Info fält 2: port index.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="host-stack-transfer-request"></a>Begäran om värd stack överföring 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Ikonen** ![ Ikon för värd stack överförings förfrågan](./media/user-guide/usbx-events/image216.png)

**Beskrivning**

Den här händelsen representerar en begäran om USBX värd stack överföring.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: slut punkt.
- Info fält 3: överförings förfrågan.
- Info fält 4: används inte.

### <a name="host-stack-transfer-request-abort"></a>Avbryt begäran om värd stack överföring 

#### <a name="internal-io-driver-get-status"></a>Status för intern I/O-drivrutin för hämtning

**Ikonen** ![ Avbryt ikon för begäran om värd stack överföring](./media/user-guide/usbx-events/image217.png)

**Beskrivning**

Den här händelsen representerar en begäran om att USBX värd stack överföring avbryts.

**Informations fält**

- Info fält 1: enhet.
- Info fält 2: slut punkt.
- Info fält 3: överförings förfrågan.
- Info fält 4: används inte.

### <a name="usbx-error"></a>USBX-fel 

#### <a name="ux_error"></a>ux_error

**Ikonen** ![ Fel ikon för U S B X](./media/user-guide/usbx-events/image218.png)

**Beskrivning**

Den här händelsen representerar en fel händelse för USBX.

**Informations fält**

- Informations fält 1: USBX-fel.
- Informations fält 2: fel namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.