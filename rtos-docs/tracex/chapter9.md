---
title: Kapitel 9 – Azure RTOS USBX-spårningshändelser
description: Det här kapitlet innehåller en beskrivning av Azure RTOS USBX-händelser som visas av TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 015e5feedd1d5e90c6491e156c2d0d57a9abaa47518868d375a34e618770d4aa
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116795407"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Kapitel 9 – Azure RTOS USBX-spårningshändelser

Det här kapitlet innehåller en beskrivning av Azure RTOS USBX-händelser som visas av TraceX. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

Följande är en lista över USBX-händelser som visas av TraceX.

| Ikon                             | Innebörd                               |
| -------------------------------- | ------------------------------------- |
| ![Aktiveringsikon för enhetsklass C D C](./media/user-guide/usbx-events/image1.png)    | **Cdc-aktivering för enhetsklass** *(ux_device_class_cdc_activate)* |
| ![Ikon för inaktiverad enhet klass C D C](./media/user-guide/usbx-events/image2.png)    | **Cdc-inaktivera för enhetsklass** *(ux_device_class_cdc_deactivate)* |
| ![Read-ikonen för Device Class C D C](./media/user-guide/usbx-events/image3.png)    | **Cdc-läsning för enhetsklass** *(ux_device_class_cdc_read)* |
| ![Skrivningsikon för enhetsklass C D C](./media/user-guide/usbx-events/image4.png)    | **Cdc-skrivning för** *enhetsklass (ux_device_class_cdc_write)* |
| ![Aktiveringsikon för enhetsklass-Dpump](./media/user-guide/usbx-events/image5.png)    | **Device Class Dpump Activate** *(ux_device_class_dpump_activate)* |
| ![Ikon för inaktiverad enhetklass-Dpump](./media/user-guide/usbx-events/image6.png)    | **Inaktivera enhetsklass -Dpump** *(ux_device_class_dpump_deactivate)* |
| ![Ikonen Läsa för enhetsklass-Dpump](./media/user-guide/usbx-events/image7.png)    | **Device Class Dpump Read** *(ux_device_class_dpump_read)* |
| ![Skrivningsikon för enhetsklass-Dpump](./media/user-guide/usbx-events/image8.png)    | **Device Class Dpump Write** *(ux_device_class_dpump_write)* |
| ![Ikonen Hid-aktivering för enhetsklass](./media/user-guide/usbx-events/image9.png)    | **Hid Activate för enhetsklass** *(ux_device_class_hid_activate)* |
| ![Ikon för inaktiverad enhetsklass](./media/user-guide/usbx-events/image10.png)    | **Inaktivera enhetsklass** *(ux_device_class_hid_deactivate)* |
| ![Ikonen Skicka med enhetsklass-Hid Descriptor](./media/user-guide/usbx-events/image11.png)    | **Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)* |
| ![Ikonen Hämta händelse för enhetsklass](./media/user-guide/usbx-events/image12.png)    | **Device Class Hid Event Get** *(ux_device_class_hid_event_get)* |
| ![Ikon för hid-händelseuppsättning för enhetsklass](./media/user-guide/usbx-events/image13.png)    | **Händelseuppsättning för enhetsklass** *(ux_device_class_hid_event_set)* |
| ![Ikonen Hämta rapport för enhetsklass](./media/user-guide/usbx-events/image14.png)    | **Device Class Hid Report Get** *(ux_device_class_hid_report_get)* |
| ![Ikon för Hid Report Set för enhetsklass](./media/user-guide/usbx-events/image15.png)    | **Rapportuppsättning för enhetsklass** *(ux_device_class_hid_report_set)* |
| ![Pima-aktiveringsikon för enhetsklass](./media/user-guide/usbx-events/image16.png)    | **Pima-aktivering för enhetsklass** *(ux_device_class_pima_activate)* |
| ![Ikon för Pima-inaktivera för enhetsklass](./media/user-guide/usbx-events/image17.png)    | **Pima-inaktivera för enhetsklass** *(ux_device_class_pima_deactivate)* |
| ![Ikonen Skicka enhetsinformation för enhetsklass Pima](./media/user-guide/usbx-events/image18.png)    | **Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)* |
| ![Ikonen Hämta händelse för enhetsklass](./media/user-guide/usbx-events/image19.png)    | **Device Class Pima Event Get** *(ux_device_class_pima_event_get)* |
| ![Händelseuppsättningsikon för Device Class Pima](./media/user-guide/usbx-events/image20.png)    | **Händelseuppsättning för enhetsklass pima** *(ux_device_class_pima_event_set)* |
| ![Pima Object Add-ikon för enhetsklass](./media/user-guide/usbx-events/image21.png)    | **Pima Object Add för enhetsklass** *(ux_device_class_pima_object_add)* |
| ![Ikonen Hämta objektdata för enhetsklass](./media/user-guide/usbx-events/image22.png)    | **Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)* |
| ![Ikonen Skicka objektdata för Enhetsklass Pima-objekt](./media/user-guide/usbx-events/image23.png)    | **Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)* |
| ![Ikonen Ta bort objekt för enhetsklass Pima](./media/user-guide/usbx-events/image24.png)    | **Borttagning av enhetsklassobjekt** *(ux_device_class_pima_object_delete)* |
| ![Ikonen Device Class Pima Object Handles Send (Pima-objekt hanterar skicka)](./media/user-guide/usbx-events/image25.png)    | **Device Class Pima Object hanterar Send** *(ux_device_class_pima_object_handles_send)* |
| ![Hämta ikon för Pima-objektinformation för enhetsklass](./media/user-guide/usbx-events/image26.png)    | **Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)* |
| ![Ikonen Skicka information om Objektinformation för enhetsklass](./media/user-guide/usbx-events/image27.png)    | **Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)* |
| ![Ikonen Skicka nummer för Enhetsklass-Pima-objekt](./media/user-guide/usbx-events/image28.png)    | **Antal skickade Pima-objekt för enhetsklass** *(ux_device_class_pima_objects_number_send)* |
| ![Ikonen Hämta partiella objektdata för Enhetsklass Pima](./media/user-guide/usbx-events/image29.png)    | **Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)* |
| ![Ikonen Skicka svar för Enhetsklass Pima](./media/user-guide/usbx-events/image30.png)    | **Pima Response Send för enhetsklass** *(ux_device_class_pima_response_send)*|
| ![Ikonen Skicka i ID Storage Pima för enhetsklass](./media/user-guide/usbx-events/image31.png)    | **Device Class Pima Storage ID Send** *(ux_device_class_pima_storage_id_send)* |
| ![Ikonen Skicka information Storage Pima för enhetsklass](./media/user-guide/usbx-events/image32.png)    | **Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)* |
| ![Aktiveringsikon för Device Class R ND I S](./media/user-guide/usbx-events/image33.png)    | **Device Class Rndis Activate** *(ux_device_class_rndis_activate)* |
| ![Ikon för inaktiverad enhet klass R ND I S](./media/user-guide/usbx-events/image34.png)    | **Inaktivera enhetsklass** *(ux_device_class_rndis_deactivate)* |
| ![Device Class R N D I S Message Keep Aliveicon](./media/user-guide/usbx-events/image35.png)    | **Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)* |
| ![Meddelandefrågeikon för Enhetsklass R ND I S](./media/user-guide/usbx-events/image36.png)    | **Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)* |
| ![Ikon för R ND I S-meddelandeåterställning för enhetsklass](./media/user-guide/usbx-events/image37.png)    | **Rndis-meddelandeåterställning för enhetsklass** *(ux_device_class_rndis_msg_reset)* |
| ![Ikon för R ND I S-meddelandeuppsättning för enhetsklass](./media/user-guide/usbx-events/image38.png)    | **Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)* |
| ![Ikon för R ND I S-paket för enhetsklass](./media/user-guide/usbx-events/image39.png)    | **Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)* |
| ![Ikonen Device Class R N D I S Packet Transmit](./media/user-guide/usbx-events/image40.png)    | **Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)* |
| ![Ikonen Enhetsklass Storage Aktivera](./media/user-guide/usbx-events/image41.png)    | **Device Class Storage Activate** *(ux_device_class_storage_activate)* |
| ![Ikon för Storage enhetsklass](./media/user-guide/usbx-events/image42.png)    | **Inaktivera Storage** *(ux_device_class_storage_deactivate)* |
| ![Ikonen Device Class Storage Format](./media/user-guide/usbx-events/image43.png)    | **Device Class Storage Format** *(ux_device_class_storage_format)* |
| ![Ikon för Storage enhetsklassförfrågan](./media/user-guide/usbx-events/image44.png)    | **Förfrågan om Storage enhetsklass** *(ux_device_class_storage_inquiry)* |
| ![Ikonen Välj Storage enhetklassläge](./media/user-guide/usbx-events/image45.png)    | **Välj Storage (ux_device_class_storage_mode_select)** för *enhetsklass* |
| ![Ikon för Storage sense i enhetsläge](./media/user-guide/usbx-events/image46.png)    | **Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)* |
| ![Ikon för Storage förhindra borttagning av media](./media/user-guide/usbx-events/image47.png)    | **Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Ikonen Device Class Storage Read (Läsa)](./media/user-guide/usbx-events/image48.png)    | **Device Class Storage Read** *(ux_device_class_storage_read)* |
| ![Ikon för Storage läsa kapacitet för enhetsklass](./media/user-guide/usbx-events/image49.png)    | **Enhet klass Storage läskapacitet** *(ux_device_class_storage_read_capacity)* |
| ![Kapacitetsikonen Storage Device Class Storage Read Format](./media/user-guide/usbx-events/image50.png)    | **Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)* |
| ![Ikon för Storage för enhetsklassläsning](./media/user-guide/usbx-events/image51.png)    | **Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)* |
| ![Ikonen Device Class Storage Request Sense](./media/user-guide/usbx-events/image52.png)    | **Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)* |
| ![Ikon för Storage start/stopp för enhetsklass](./media/user-guide/usbx-events/image53.png)    | **Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)* |
| ![Ikon för Storage test för enhetsklass](./media/user-guide/usbx-events/image54.png)    | **Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)* |
| ![Ikonen Device Class Storage Verify (Verifiera)](./media/user-guide/usbx-events/image55.png)    | **Device Class Storage Verify** *(ux_device_class_storage_verify)* |
| ![Ikonen Device Class Storage Write](./media/user-guide/usbx-events/image56.png)    | **Device Class Storage Write** *(ux_device_class_storage_write)* |
| ![Ikonen Hämta alternativ inställning för enhetsstack](./media/user-guide/usbx-events/image57.png)    | **Alternativ inställning för enhetsstack hämta** *(ux_device_stack_alternate_setting_get)* |
| ![Ikon för alternativ inställningsuppsättning för enhetsstack](./media/user-guide/usbx-events/image58.png)    | **Alternativ inställningsuppsättning för enhetsstack** *(ux_device_stack_alternate_setting_set)* |
| ![Ikon för enhetsstacksklassregister](./media/user-guide/usbx-events/image59.png)    | **Device Stack-klassregister** *(ux_device_stack_class_register)* |
| ![Ikonen Rensa funktion i enhetsstack](./media/user-guide/usbx-events/image60.png)    | **Rensa funktion för enhetsstack** *(ux_device_stack_clear_feature)* |
| ![Ikonen Hämta för konfiguration av enhetsstack](./media/user-guide/usbx-events/image61.png)    | **Hämta (hämta) konfiguration** *av enhetsstack (ux_device_stack_configuration_get)* |
| ![Ikon för konfigurationsuppsättning för enhetsstack](./media/user-guide/usbx-events/image62.png)    | **Konfigurationsuppsättning för enhetsstack** *(ux_device_stack_configuration_set)* |
| ![Ikon för Anslut enhetsstack](./media/user-guide/usbx-events/image63.png)    | **Device Stack Anslut** *(ux_device_stack_connect)* |
| ![Ikonen Skicka enhetsstacksbeskrivning](./media/user-guide/usbx-events/image64.png)    | **Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)* |
| ![Ikon för frånkoppling av enhetsstack](./media/user-guide/usbx-events/image65.png)    | **Koppla från enhetsstack** *(ux_device_stack_disconnect)* |
| ![Ikon för slutpunktstopp för enhetsstack](./media/user-guide/usbx-events/image66.png)    | **Slutpunktstopp för enhetsstack** *(ux_device_stack_endpoint_stall)* |
| ![Ikonen Hämta status för enhetsstack](./media/user-guide/usbx-events/image67.png)    | **Hämta status för enhetsstack** *(ux_device_stack_get_status)* |
| ![Aktiveringsikon för värd för enhetsstack](./media/user-guide/usbx-events/image68.png)    | **Aktivering av värd för enhetsstack** *(ux_device_stack_host_wakeup)* |
| ![Ikonen Initiera i enhetsstack](./media/user-guide/usbx-events/image69.png)    | **Device Stack Initialize** *(ux_device_stack_initialize)* |
| ![Ikonen Ta bort gränssnitt för enhetsstack](./media/user-guide/usbx-events/image70.png)    | **Ta bort gränssnitt för enhetsstack** *(ux_device_stack_interface_delete)* |
| ![Ikonen Hämta för Device Stack-gränssnitt](./media/user-guide/usbx-events/image71.png)    | **Device Stack Interface Get** *(ux_device_stack_interface_get)* |
| ![Ikon för Enhetsstack-gränssnittsuppsättning](./media/user-guide/usbx-events/image72.png)    | **Device Stack-gränssnittsuppsättning** *(ux_device_stack_interface_set)* |
| ![Ikon för enhetsstackuppsättningsfunktion](./media/user-guide/usbx-events/image73.png)    | **Set-funktion för enhetsstack** *(ux_device_stack_set_feature)* |
| ![Ikonen Avbryt överföring av enhetsstack](./media/user-guide/usbx-events/image74.png)    | **Avbryt överföring av enhetsstack** *(ux_device_stack_transfer_abort)* |
| ![*Ikonen Överför alla förfrågningar om överföring av enhetsstack](./media/user-guide/usbx-events/image75.png)    | **Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)* |
| ![Ikonen Överföringsbegäran för enhetsstack](./media/user-guide/usbx-events/image76.png)    | **Begäran om överföring av enhetsstack** *(ux_device_stack_transfer_request)* |
| ![Aktiveringsikon för värdklass somix](./media/user-guide/usbx-events/image77.png)    | **Aktivera Host Class Asix** *(ux_host_class_asix_activate)* |
| ![Ikon för inaktivera värdklass som asix](./media/user-guide/usbx-events/image78.png)    | **Inaktivera värdklass somix** *(ux_host_class_asix_deactivate)* |
| ![Meddelandeikon för avbrottsmeddelande för värdklass asix](./media/user-guide/usbx-events/image79.png)    | **Avbrottsmeddelande för värdklass Asix** *(ux_host_class_asix_interrupt_notification)* |
| ![Ikon för att läsa värdklass somix](./media/user-guide/usbx-events/image80.png)    | **Host Class Asix Read** *(ux_host_class_asix_read)* |
| ![Skrivikon för värdklass somix](./media/user-guide/usbx-events/image81.png)    | **Host Class Asix Write** *(ux_host_class_asix_write)* |
| ![Aktiveringsikon för värdklassljud](./media/user-guide/usbx-events/image82.png)    | **Aktivera aktivering av värdklassljud** *(ux_host_class_audio_activate)* |
| ![Ikonen Hämta värde för värdklassljudkontroll](./media/user-guide/usbx-events/image83.png)    | **Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)* |
| ![Ikon för värdeuppsättning för värdklassljudkontroll](./media/user-guide/usbx-events/image84.png)    | **Värdeuppsättning för värdklassljudkontroll** *(ux_host_class_audio_control_value_set)* |
| ![Inaktivera ikon för värdklassljud](./media/user-guide/usbx-events/image85.png)    | **Inaktivera värdklassljud** *(ux_host_class_audio_deactivate)* |
| ![Ikon för ljudläsning för värdklass](./media/user-guide/usbx-events/image86.png)    | **Ljudläsning för värdklass** *(ux_host_class_audio_read)* |
| ![Hämta-ikonen För sampling av ljudströmning för värdklass](./media/user-guide/usbx-events/image87.png)    | **Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Ikon för uppsättning för insamling av ljudströmning för värdklass](./media/user-guide/usbx-events/image88.png)    | **Samplingsuppsättning för ljudströmning för värdklass** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Ikon för ljudskrivning för värdklass](./media/user-guide/usbx-events/image89.png)    | **Ljudskrivning för värdklass** *(ux_host_class_audio_write)* |
| ![Aktiveringsikon för värdklass C D C A C M](./media/user-guide/usbx-events/image90.png)    | **Aktivering av Host Class Cdc Acm** *(ux_host_class_cdc_acm_activate)* |
| ![Ikon för inaktiverad värdklass C D C A C M](./media/user-guide/usbx-events/image91.png)    | **Inaktivera Värdklass Cdc Acm** *(ux_host_class_cdc_acm_deactivate)* |
| ![Ikon för värdklass C D C A C M I O C T L i pipe](./media/user-guide/usbx-events/image92.png)    | **Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Ikonen Avbryt pipe för värdklass C D C A C M I O C T L Avbryt ut pipe](./media/user-guide/usbx-events/image93.png)    | **Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Ikon för att hämta enhetsstatus för värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image94.png)    | **Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Ikon för att hämta linjekodning för värdklass C D C A C M M I O C T L Get Line Coding](./media/user-guide/usbx-events/image95.png)    | **Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Ikon för återanrop av meddelanden från värdklass C D C A C M M I O C T L](./media/user-guide/usbx-events/image96.png)    | **Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Skicka brytikon för värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image97.png)    | **Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Kodningsikon för raduppsättningskodning för värdklass C D C A C M M I O C T L](./media/user-guide/usbx-events/image98.png)    | **Kodning av värdklass cdc Acm Ioctl set line** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Ikon för ange radtillstånd för värdklass C D C A C M M I O C T L](./media/user-guide/usbx-events/image99.png)    | **Värdklass Cdc Acm Ioctl Ange radtillstånd** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Ikon för att läsa värdklass C D C A C M](./media/user-guide/usbx-events/image100.png)    | **Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)* |
| ![Startikon för värdklass C D C A C M-mottagning](./media/user-guide/usbx-events/image101.png)    | **Värdklass Cdc Acm Mottagningsstart** *(ux_host_class_cdc_acm_reception_start)* |
| ![Ikon för värdklass C D C A C M mottagningsstopp](./media/user-guide/usbx-events/image102.png)    | **Host Class Cdc Acm Mottagningsstopp** *(ux_host_class_cdc_acm_reception_stop)* |
| ![Skrivikon för Värdklass C D C A C M](./media/user-guide/usbx-events/image103.png)    | **Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)* |
| ![Aktiveringsikon för värdklass-Dpump](./media/user-guide/usbx-events/image104.png)    | **Aktivera värdklass-Dpump** *(ux_host_class_dpump_activate)* |
| ![Ikon för inaktivera värdklass-Dpump](./media/user-guide/usbx-events/image105.png)    | **Inaktivera värdklass Dpump** *(ux_host_class_dpump_deactivate)* |
| ![Ikon för värdklass-Dpump- läsning](./media/user-guide/usbx-events/image106.png)    | **Host Class Dpump Read** *(ux_host_class_dpump_read)* |
| ![Skrivikon för värdklass-Dpump](./media/user-guide/usbx-events/image107.png)    | **Host Class Dpump Write** *(ux_host_class_dpump_write)* |
| ![Ikonen Hid-aktivering för värdklass](./media/user-guide/usbx-events/image108.png)    | **Hid-aktivering för värdklass** *(ux_host_class_hid_activate)* |
| ![Ikon för hid-klientregister för värdklass](./media/user-guide/usbx-events/image109.png)    | **Hid-klientregister för värdklass** *(ux_host_class_hid_client_register)* |
| ![Ikon för inaktivera värdklassinaktivering](./media/user-guide/usbx-events/image110.png)    | **Inaktivera värdklass hid** *(ux_host_class_hid_deactivate)* |
| ![Ikonen Hid Idle Get för värdklass](./media/user-guide/usbx-events/image111.png)    | **Hid Idle Get** *(ux_host_class_hid_idle_get) för värdklass* |
| ![Ikon för Hid Idle Set för värdklass](./media/user-guide/usbx-events/image112.png)    | **Hid Idle Set för värdklass** *(ux_host_class_hid_idle_set)* |
| ![Aktiveringsikon för värdklass-hid-tangentbord](./media/user-guide/usbx-events/image113.png)    | **Aktivering av hid-tangentbord för** *värdklass (ux_host_class_hid_keyboard_activate)* |
| ![Ikon för inaktivera tangentbord för värdklass hid](./media/user-guide/usbx-events/image114.png)    | **Inaktivera tangentbord för värdklass** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Aktiveringsikon för värdklass för hid-mus](./media/user-guide/usbx-events/image115.png)    | **Aktivering av mus för värdklass hid** *(ux_host_class_hid_mouse_activate)* |
| ![Ikon för inaktiverad mus för värdklass](./media/user-guide/usbx-events/image116.png)    | **Inaktivera mus för värdklass** *(ux_host_class_hid_mouse_deactivate)* |
| ![Aktiveringsikon för värdklass hid-fjärrstyrning](./media/user-guide/usbx-events/image117.png)    | **Aktivering av fjärrstyrning för värdklass** *(ux_host_class_hid_remote_control_activate)* |
| ![Ikon för inaktivera fjärrstyrning för värdklass hid](./media/user-guide/usbx-events/image118.png)    | **Inaktivera fjärrstyrning av värdklass** *(ux_host_class_hid_remote_control_deactivate)* |
| ![Ikonen Hämta rapport för värdklass](./media/user-guide/usbx-events/image119.png)    | **Host Class Hid Report Get** *(ux_host_class_hid_report_get)* |
| ![Ikon för hid-rapportuppsättning för värdklass](./media/user-guide/usbx-events/image120.png)    | **Hid-rapportuppsättning för värdklass** *(ux_host_class_hid_report_set)* |
| ![Aktiveringsikon för värdklasshubb](./media/user-guide/usbx-events/image121.png)    | **Aktivera värdklasshubb** *(ux_host_class_hub_activate)* |
| ![Ikon för ändrings detect för värdklasshubb](./media/user-guide/usbx-events/image122.png)    | **Ändrings detect för värdklasshubb** *(ux_host_class_hub_change_detect)* |
| ![*Inaktivera ikon för värdklasshubb](./media/user-guide/usbx-events/image123.png)    | **Inaktivera värdklasshubb** *(ux_host_class_hub_deactivate)* |
| ![Ikonen Ändra anslutningsprocess för värdklasshubbport](./media/user-guide/usbx-events/image124.png)    | **Process för portändringsanslutning för värdklasshubb** *(ux_host_class_hub_port_change_connection_process)* |
| ![Ikonen Aktivera process för värdklasshubbport](./media/user-guide/usbx-events/image125.png)    | **Aktivera process för portändring för värdklasshubb** *(ux_host_class_hub_port_change_enable_process)* |
| ![Portändring för värdklasshubb över aktuell process-ikon](./media/user-guide/usbx-events/image126.png)    | **Portändring för värdklasshubb över aktuell process** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Ikon för ändringsåterställningsprocess för värdklasshubbport](./media/user-guide/usbx-events/image127.png)    | **Process för ändringsåterställning av värdklasshubbport** *(ux_host_class_hub_port_change_reset_process)* |
| ![Ikon för ändring av pausprocess för värdklasshubbport](./media/user-guide/usbx-events/image128.png)    | **Pausprocess för portändring för värdklasshubb** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Aktiveringsikon för värdklass-Pima](./media/user-guide/usbx-events/image129.png)    | **Aktivering av värdklass -Pima** *(ux_host_class_prima_activate)* |
| ![Ikon för att inaktivera Pima för värdklass](./media/user-guide/usbx-events/image130.png)    | **Inaktivera Värdklass Pima** *(ux_host_class_pima_deactivate)* |
| ![Ikonen Hämta information om värdklassenhetsinformation för värdklass](./media/user-guide/usbx-events/image131.png)    | **Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)* |
| ![Ikon för återställning av värdklassenhet](./media/user-guide/usbx-events/image132.png)    | **Återställning av värdklass för Pima-enhet** *(ux_host_class_pima_device_reset)* |
| ![Meddelandeikon för värdklass-Pima](./media/user-guide/usbx-events/image133.png)    | **Pima-meddelande för värdklass** *(ux_host_class_pima_notification)* |
| ![Pima Number Objects Get-ikon för värdklass](./media/user-guide/usbx-events/image134.png)    | **Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)* |
| ![Stängningsikon för värdklass-Pima-objekt](./media/user-guide/usbx-events/image135.png)    | **Pima Object Close för värdklass** *(ux_host_class_pima_object_close)* |
| ![Pima Object Copy-ikon för värdklass](./media/user-guide/usbx-events/image136.png)    | **Pima Object Copy för värdklass** *(ux_host_class_pima_object_copy)* |
| ![Ikonen Ta bort objekt för värdklass Pima](./media/user-guide/usbx-events/image137.png)    | **Borttagning av objekt för värdklass** *(ux_host_class_pima_object_delete)* |
| ![Pima Object Get-ikon för värdklass](./media/user-guide/usbx-events/image138.png)    | **Host Class Pima Object Get** *(ux_host_class_pima_object_get)* |
| ![Pima Object Info Hämta-ikon för värdklass](./media/user-guide/usbx-events/image139.png)    | **Information om Pima-objekt för värdklass** *hämta (ux_host_class_pima_object_info_get)* |
| ![Skicka ikon för Pima-objektinformation för värdklass](./media/user-guide/usbx-events/image140.png)    | **Skicka information om Pima-objekt för värdklass** *(ux_host_class_pima_object_info_send)* |
| ![Flytta objektikon för värdklass Pima](./media/user-guide/usbx-events/image141.png)    | **Flytta objekt för värdklass** *(ux_host_class_pima_object_move)* |
| ![Ikonen Skicka Pima-objekt för värdklass](./media/user-guide/usbx-events/image142.png)    | **Skicka Pima-objekt för värdklass** *(ux_host_class_pima_object_send)* |
| ![Ikonen För att avbryta överföring av värdklassobjekt i Pima-klass](./media/user-guide/usbx-events/image143.png)    | **Abort av objektöverföring för värdklass** *(ux_host_class_object_transfer_abort)* |
| ![Pima Read-ikon för värdklass](./media/user-guide/usbx-events/image144.png)    | **Host Class Pima Read** *(ux_host_class_pima_read)* |
| ![Ikonen För att avbryta begäran för värdklass Pima](./media/user-guide/usbx-events/image145.png)    | **Begäran om att avbryta värdklassens Pima** *(ux_host_class_pima_request_cancel)* |
| ![Ikon för Pima-sessionsslut för värdklass](./media/user-guide/usbx-events/image146.png)    | **Sessionsslut för värdklass Pima** *(ux_host_class_pima_session_close)* |
| ![Ikonen Öppna för värdklasssession för Pima](./media/user-guide/usbx-events/image147.png)    | **Pima-session för värdklass öppen** *(ux_host_class_pima_session_open)* |
| ![Ikon för att hämta Storage-ID:n för värdklass](./media/user-guide/usbx-events/image148.png)    | **Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)* |
| ![Pima-ikonen Storage hämta information för värdklass](./media/user-guide/usbx-events/image149.png)    | **Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)* |
| ![Pima Thumb Get-ikon för värdklass](./media/user-guide/usbx-events/image150.png)    | **Pima Thumb Get för värdklass** *(ux_host_class_pima_thumb_get)* |
| ![Pima Write-ikon för värdklass](./media/user-guide/usbx-events/image151.png)    | **Host Class Pima Write** *(ux_host_class_pima_write)* |
| ![Aktiveringsikon för värdklassskrivare](./media/user-guide/usbx-events/image152.png)    | **Aktivera värdklassskrivare** *(ux_host_class_printer_activate)* |
| ![Ikon för att inaktivera värdklassskrivare](./media/user-guide/usbx-events/image153.png)    | **Inaktivera värdklassskrivare** *(ux_host_class_printer_deactivate)* |
| ![Ikonen Hämta namn på värdklassskrivare](./media/user-guide/usbx-events/image154.png)    | **Hämta (ux_host_class_printer_name_get)** *för värdklassskrivare* |
| ![Ikon för skrivarläsning för värdklass](./media/user-guide/usbx-events/image155.png)    |  **Skrivarläsning för värdklass** *(ux_host_class_printer_read)* |
| ![Ikon för mjuk återställning av värdklassskrivare](./media/user-guide/usbx-events/image156.png)    | **Mjuk återställning av värdklassskrivare** *(ux_host_class_printer_soft_reset)* |
| ![Ikonen Hämta status för värdklassskrivare](./media/user-guide/usbx-events/image157.png)    | **Hämta status för värdklassskrivare** *(ux_host_class_printer_status_get)* |
| ![Skrivikon för värdklassskrivare](./media/user-guide/usbx-events/image158.png)    | **Skriva värdklassskrivare** *(ux_host_class_printer_write)* |
| ![Aktiveringsikon för värdklass](./media/user-guide/usbx-events/image159.png)    | **Aktivering av värdklass** *(ux_host_class_prolific_activate)* |
| ![Ikon för inaktivera värdklass](./media/user-guide/usbx-events/image160.png)    | **Inaktivera värdklass prolific** *(ux_host_class_prolific_deactivate)* |
| ![Host Class Prolific I O C T L Abort In Pipe-ikon](./media/user-guide/usbx-events/image161.png)    | **Prolific Ioctl Abort In Pipe** (ux_host_class_prolific_ioctl_abort_in_pipe) (Host Class Prolific Ioctl Abort In Pipe *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Ikon för värdklassprolific I O C T L Abort Out Pipe](./media/user-guide/usbx-events/image162.png)    | **Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Ikon för att hämta enhetsstatus för värdklassprolific I O C T L](./media/user-guide/usbx-events/image163.png)    | **Hämta enhetsstatus för värdklass prolific Ioctl** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![Ikon för att hämta radkodning för värdklassprolific I O C T L](./media/user-guide/usbx-events/image164.png)    | **Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Ikon för rensning av värdklassprolific I O C T L](./media/user-guide/usbx-events/image165.png)    | **Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)* |
| ![Ikon för ändring av enhetsstatus för värdklass prolific I O C T L Report](./media/user-guide/usbx-events/image166.png)    | **Ändring av enhetsstatus för värdklass prolific Ioctl -rapport** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Ikonen Skicka paus för värdklassprolific I O C T L](./media/user-guide/usbx-events/image167.png)    | **Skicka paus för värdklass prolific Ioctl** *(ux_host_class_prolific_ioctl_send_break)* |
| ![Ikon för radkodning för värdklassprolific I O C T L Set Line](./media/user-guide/usbx-events/image168.png)    | **Kodning av rad för värdklassprolific Ioctl Set** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Ikon för ange radtillstånd för värdklassprolific I O C T L Set Line State](./media/user-guide/usbx-events/image169.png)    | **Radtillstånd för värdklassproocific Ioctl Set** *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![Ikon för värdklassläsning](./media/user-guide/usbx-events/image170.png)    | **Prolific Read för värdklass** *(ux_host_class_prolific_read)* |
| ![Startikon för värdklassmottagande](./media/user-guide/usbx-events/image171.png)    | **Host Class Prolific Mottagningsstart** *(ux_host_class_prolific_reception_start)* |
| ![Stoppikon för värdklassmottagande](./media/user-guide/usbx-events/image172.png)    | **Host Class Prolific Mottagningsstopp** *(ux_host_class_prolific_reception_stop)* |
| ![Ikon för skrivskydd för värdklass](./media/user-guide/usbx-events/image173.png)    | **Prolific Write för värdklass** *(ux_host_class_prolific_write)* |
| ![Ikonen Aktivera Storage värdklass](./media/user-guide/usbx-events/image174.png)    | **Aktivera värdklass Storage** *(ux_host_class_storage_activate)* |
| ![Ikon för Storage inaktivera för värdklass](./media/user-guide/usbx-events/image175.png)    | **Inaktivera Storage värdklass** *(ux_host_class_storage_deactivate)* |
| ![Hämta ikon Storage värdklass för mediekapacitet](./media/user-guide/usbx-events/image176.png)    | **Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)* |
| ![Hämta-Storage för värdklass i Media Format-kapacitet](./media/user-guide/usbx-events/image177.png)    | **Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Ikon för Storage mediamontering för värdklass](./media/user-guide/usbx-events/image178.png)    | **Värdklass för Storage Media Mount** (ux_host_class_storage_media_mount)* |
| ![Ikonen Storage Media Open för värdklass](./media/user-guide/usbx-events/image179.png)    | **Host Class Storage Media Open** *(ux_host_class_storage_media_open)* |
| ![Ikon för Storage medieläsning för värdklass](./media/user-guide/usbx-events/image180.png)    | **Värdklass för Storage medieläsning** *(ux_host_class_storage_media_read)* |
| ![Ikon för Storage medieskrivning för värdklass](./media/user-guide/usbx-events/image181.png)    | **Host Class Storage Media Write** *(ux_host_class_storage_media_write)* |
| ![Ikon för Storage Begär sense för värdklass](./media/user-guide/usbx-events/image182.png)    | **Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)* |
| ![Ikon för Storage starta/stoppa för värdklass](./media/user-guide/usbx-events/image183.png)    | **Startstopp Storage värdklass** *(ux_host_class_storage_start_stop)* |
| ![Ikon för Storage för redo Storage för värdklass](./media/user-guide/usbx-events/image184.png)    | **Test av Storage för värdklass** *(ux_host_class_storage_activate)* |
| ![Skapa ikon för värdstackklassinstans](./media/user-guide/usbx-events/image185.png)    | **Skapa värdstacksklassinstans** *(ux_host_stack_class_instance_create)* |
| ![Ta bort ikon för värdstackklassinstans](./media/user-guide/usbx-events/image186.png)    | **Destroy för värdstackklassinstans** *(ux_host_stack_class_instance_destroy)* |
| ![Ikonen Ta bort konfiguration av värdstack](./media/user-guide/usbx-events/image187.png)    | **Ta bort konfiguration av värdstack** *(ux_host_stack_configuration_delete)* |
| ![Ikon för konfiguration av värdstackskonfiguration](./media/user-guide/usbx-events/image188.png)    | **Konfigurationsuppräkning för värdstack** *(ux_host_stack_configuration_enumerate)* |
| ![Ikonen Skapa instans för konfigurationsinstans för värdstack](./media/user-guide/usbx-events/image189.png)    | **Skapa en konfigurationsinstans för värdstack** *(ux_host_stack_configuration_instance_create)* |
| ![Ikon för borttagning av konfigurationsinstans för värdstack](./media/user-guide/usbx-events/image190.png)    | **Ta bort konfigurationsinstans för värdstack** *(ux_host_stack_configuration_instance_delete)* |
| ![Ikon för konfigurationsuppsättning för värdstack](./media/user-guide/usbx-events/image191.png)    | **Konfigurationsuppsättning för värdstack** *(ux_host_stack_configuration_set)* |
| ![Ikon för enhetsadressuppsättning för värdstack](./media/user-guide/usbx-events/image192.png)    | **Enhetsadressuppsättning för värdstack** *(ux_host_stack_device_set)* |
| ![Ikonen Hämta för enhetskonfiguration för värdstack](./media/user-guide/usbx-events/image193.png)    | **Hämta enhetskonfiguration för värdstack** *(ux_host_stack_device_configuration_get)* |
| ![Ikon för enhetskonfiguration för värdstack välj](./media/user-guide/usbx-events/image194.png)    | **Välj enhetskonfiguration för värdstack** *(ux_host_stack_device_configuration_select)* |
| ![Ikonen Läsa för enhetsbeskrivning i värdstack](./media/user-guide/usbx-events/image195.png)    | **Enhetsbeskrivning för värdstack** *(ux_host_stack_device_descriptor_read)* |
| ![Ikonen Hämta för värdstacksenhet](./media/user-guide/usbx-events/image196.png)    | **Hämta värdstackenhet** (ux_host_stack_device_get) |
| ![Ikonen Ta bort värdstacksenhet](./media/user-guide/usbx-events/image197.png)    | **Ta bort värdstackenhet** (ux_host_stack_device_get) |
| ![Ikon för kostnadsfri resurs för värdstackenhet](./media/user-guide/usbx-events/image198.png)    | **Resurs kostnadsfri för värdstackenhet** (ux_host_stack_device_resource_free) |
| ![Ikonen Skapa slutpunktsinstans för värdstack](./media/user-guide/usbx-events/image199.png)    | **Skapa slutpunktsinstans för värdstack** (ux_host_stack_endpoint_instance_create) |
| ![Ikonen Ta bort slutpunktsinstans för värdstack](./media/user-guide/usbx-events/image200.png)    | **Ta bort slutpunktsinstans för värdstack** (ux_host_stack_endpoint_instance_delete) |
| ![Ikon för slutpunktsåterställning för värdstack](./media/user-guide/usbx-events/image201.png)    | **Slutpunktsåterställning för värdstack** (ux_host_stack_endpoint_reset) |
| ![Ikonen Avbryt avslutsöverföring av värdstack](./media/user-guide/usbx-events/image202.png)    | **Migrering av slutpunktsöverföring av värdstack** (ux_host_stack_endpoint_transfer_abort) |
| ![Registerikon för värdstackvärdstyrenhet](./media/user-guide/usbx-events/image203.png)    | **Host Stack Host Controller Register** *(ux_host_stack_hcd_register)* |
| ![Initieringsikon för värdstack](./media/user-guide/usbx-events/image204.png)    | **Initiera värdstack** *(ux_host_stack_initialize)* |
| ![Ikonen Hämta för gränssnittsslutpunkt för värdstack](./media/user-guide/usbx-events/image205.png)    | **Hämta (ux_host_stack_interface_endpoint_get)** *för gränssnittsslutpunkt för värdstack* |
| ![Ikonen Skapa gränssnittsinstans för värdstack](./media/user-guide/usbx-events/image206.png)    | **Skapa gränssnittsinstans för värdstack** *(ux_host_stack_interface_instance_create)* |
| ![Ikonen Ta bort gränssnittsinstans för värdstack](./media/user-guide/usbx-events/image207.png)    | **Ta bort gränssnittsinstans för värdstack** *(ux_host_stack_interface_instance_delete)* |
| ![Ikon för gränssnittsuppsättning för värdstack](./media/user-guide/usbx-events/image208.png)    | **Gränssnittsuppsättning för värdstack** *(ux_host_stack_interface_set)* |
| ![Gränssnittsinställning för värdstack välj ikon](./media/user-guide/usbx-events/image209.png)    | **Gränssnittsinställning för värdstack** *(ux_host_stack_interface_setting_select)* |
| ![Ikonen Skapa ny konfiguration för värdstack](./media/user-guide/usbx-events/image210.png)    | **Skapa ny konfiguration för värdstack** *(ux_host_stack_new_configuration_create)* |
| ![Ikonen Skapa ny enhet för värdstack](./media/user-guide/usbx-events/image211.png)    | **Skapa ny enhet med värdstack** *(ux_host_stack_new_device_create)* |
| ![Ikonen Skapa ny slutpunkt för värdstack](./media/user-guide/usbx-events/image212.png)    | **Skapa ny slutpunkt för värdstack** *(ux_host_stack_new_endpoint_create)* |
| ![Ikon för ändringsprocess för värdstackens rothubb](./media/user-guide/usbx-events/image213.png)    | **Ändringsprocess för värdstackens rothubb** *(ux_host_stack_rh_change_process)* |
| ![Ikon för extrahering av värdstackens rothubbenhet](./media/user-guide/usbx-events/image214.png)    | **Extrahering av rothubben för värdstack** *(ux_host_stack_rh_device_extraction)* |
| ![Ikon för infogning av rothubbenhet för värdstack](./media/user-guide/usbx-events/image215.png)    | **Infogning av rothubbenhet för värdstack** *(ux_host_stack_rh_device_insertion)* |
| ![Ikon för begäran om överföring av värdstack](./media/user-guide/usbx-events/image216.png)    | **Begäran om överföring av värdstack** *(ux_host_stack_transfer_request)* |
| ![Ikonen Avbryt begäran om överföring av värdstack](./media/user-guide/usbx-events/image217.png)    | **Begäran om att avbryta överföring av värdstack** *(ux_host_stack_transfer_request_abort)* |
| ![Ikon för U S B X-fel](./media/user-guide/usbx-events/image218.png)    | **USBX-fel** *(ux_error)* |

## <a name="event-descriptions"></a>Händelsebeskrivningar

Följande sidor beskriver USBX-spårningshändelser.

### <a name="device-class-cdc-activate"></a>Cdc-aktivering för enhetsklass 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Ikon** ![ Aktiveringsikon för enhetsklass C D C](./media/user-guide/usbx-events/image1.png)

**Beskrivning**

Den här händelsen representerar en CDC-aktiveringshändelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-cdc-deactivate"></a>Cdc-inaktivera för enhetsklass 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Ikon** ![ Ikon för inaktiverad enhet klass C D C](./media/user-guide/usbx-events/image2.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass cdc inaktivera.

Informationsfält 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-cdc-read"></a>Cdc Read för enhetsklass 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Ikon** ![ Read-ikonen för Device Class C D C](./media/user-guide/usbx-events/image3.png)

**Beskrivning**

Den här händelsen representerar en CDC-läshändelse för USBX-enhetsklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="device-class-cdc-write"></a>Cdc-skrivning för enhetsklass 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Ikon** ![ Skrivningsikon för enhetsklass C D C](./media/user-guide/usbx-events/image4.png)

**Beskrivning**

Den här händelsen representerar en CDC-skrivhändelse för USBX-enhetsklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="device-class-dpump-activate"></a>Aktivering av enhetsklass-Dpump 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Ikon** ![ Aktiveringsikon för enhetsklass-Dpump](./media/user-guide/usbx-events/image5.png)

**Beskrivning**

Den här händelsen representerar en aktiveringshändelse för USBX-enhetsklass Dpump.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-dpump-deactivate"></a>Inaktivera enhetsklass-Dpump 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Ikon** ![ Ikon för inaktiverad enhetklass-Dpump](./media/user-guide/usbx-events/image6.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Dpump Inaktivera händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-dpump-read"></a>Device Class Dpump Read 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Ikon** ![ Ikonen Läsa för enhetsklass-Dpump](./media/user-guide/usbx-events/image7.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Dpump Read-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Buffert.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="device-class-dpump-write"></a>Device Class Dpump Write 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Ikon** ![ Skrivningsikon för enhetsklass-Dpump](./media/user-guide/usbx-events/image8.png)

**Beskrivning**

Den här händelsen representerar en skrivningshändelse för USBX-enhetsklass Dpump.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Datapekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-activate"></a>Hid-aktivering för enhetsklass 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Ikon** ![ Ikonen Hid-aktivering för enhetsklass](./media/user-guide/usbx-events/image9.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass hid activate-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-deactivate"></a>Inaktivera enhetsklass 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Ikon** ![ Ikonen Hid-inaktivera för enhetsklass](./media/user-guide/usbx-events/image10.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass som hid-inaktiverar händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-descriptor-send"></a>Device Class Hid Descriptor Send 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Ikon** ![ Ikonen Skicka med Enhetsklass Hid Descriptor](./media/user-guide/usbx-events/image11.png)

**Beskrivning**

Den här händelsen representerar en USBX Device Class Hid Descriptor Send Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Beskrivningstyp.
- Informationsfält 3: Begärandeindex.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-event-get"></a>Hämta hid-händelse för enhetsklass 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Ikon** ![ Ikonen Hämta händelse för enhetsklass](./media/user-guide/usbx-events/image12.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass, Hid Event Get Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-event-set"></a>Händelseuppsättning för enhetsklass hid 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Ikon** ![ Ikon för hid-händelseuppsättning för enhetsklass](./media/user-guide/usbx-events/image13.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass hid-händelseuppsättning.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-report-get"></a>Hämta hid-rapport för enhetsklass 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Ikon** ![ Ikonen Hämta rapport för enhetsklass](./media/user-guide/usbx-events/image14.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass, Hid Report Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Beskrivningstyp.
- Informationsfält 3: Begärandeindex.
- Informationsfält 4: Används inte.

### <a name="device-class-hid-report-set"></a>Rapportuppsättning för enhetsklass hid 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Ikon** ![ Ikon för hid-rapportuppsättning för enhetsklass](./media/user-guide/usbx-events/image15.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass för hid report set-händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Beskrivningstyp.
- Informationsfält 3: Begärandeindex.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-activate"></a>Pima-aktivering för enhetsklass

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Ikon** ![ Ikon för Pima-aktivering för enhetsklass](./media/user-guide/usbx-events/image16.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklasshändelse för aktivering av Pima.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-deactivate"></a>Pima för enhetsklass – inaktivera 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Ikon** ![ Pima-ikonen Inaktivera för enhetsklass](./media/user-guide/usbx-events/image17.png)

**Beskrivning**

Den här händelsen representerar en Pima-inaktiverad händelse för USBX-enhetsklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-device-info-send"></a>Skicka enhetsinformation för enhetsklass 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Ikon** ![ Ikonen Skicka enhetsinformation för Enhetsklass Pima](./media/user-guide/usbx-events/image18.png)

**Beskrivning**

Den här händelsen representerar en Pima Device Info Send-händelse för USBX-enhetsklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.

### <a name="device-class-pima-event-get"></a>Hämta händelse för enhetsklass 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Ikon** ![ Ikonen Hämta händelse för enhetsklass](./media/user-guide/usbx-events/image19.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass-Pima Event Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Pima-händelse.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-event-set"></a>Händelseuppsättning för enhetsklass 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Ikon** ![ Händelseuppsättningsikon för Device Class Pima](./media/user-guide/usbx-events/image20.png)

**Beskrivning**

Den här händelsen representerar en HÄNDELSEuppsättningshändelse för USBX-enhetsklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Pima-händelse.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-object-add"></a>Pima-objekt för enhetsklass – Lägg till 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Ikon** ![ Pima Object-ikonen Lägg till för enhetsklass](./media/user-guide/usbx-events/image21.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Add-händelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-object-data-get"></a>Hämta Pima-objektdata för enhetsklass 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Ikon** ![ Pima Object Data Hämta-ikon för enhetsklass](./media/user-guide/usbx-events/image22.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Data Get-händelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-object-data-send"></a>Skicka Pima-objektdata för enhetsklass 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Ikon** ![ Ikonen Skicka Pima-objektdata för enhetsklass](./media/user-guide/usbx-events/image23.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Data Send-händelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-object-delete"></a>Ta bort Pima-objekt för enhetsklass 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Ikon** ![ Ikonen Ta bort objekt för enhetsklass](./media/user-guide/usbx-events/image24.png)

**Beskrivning**

Den här händelsen representerar en BORTTAGNINGshändelse för ETT USBX-enhetsklassobjekt.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-object-handles-send"></a>Device Class Pima Object Handles Send 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Ikon** ![ Ikonen Skicka med Pima-objekt i enhetsklass](./media/user-guide/usbx-events/image25.png)

**Beskrivning**

Den här händelsen representerar ett Pima-objekt i USBX-enhetsklassen som hanterar skicka händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Storage ID.
- Informationsfält 3: Objektformatkod.
- Informationsfält 4: Objektassociation.

### <a name="device-class-pima-object-info-get"></a>Information om Pima-objekt för enhetsklass hämta 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikon** ![ Pima Object Info Hämta-ikon för enhetsklass](./media/user-guide/usbx-events/image26.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Info Get-händelse för USBX-enhetsklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-object-info-send"></a>Skicka information om Pima-objekt för enhetsklass 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikon** ![ Ikonen Skicka information om Objektinformation för enhetsklass](./media/user-guide/usbx-events/image27.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Info Send-händelse för USBX-enhetsklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-objects-number-send"></a>Antal skickade Pima-objekt för enhetsklass 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Ikon** ![ Ikonen Skicka nummer för Enhetsklass-Pima-objekt](./media/user-guide/usbx-events/image28.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Number Send-händelse för USBX-enhetsklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Storage-ID.
- Informationsfält 3: Objektformatkod.
- Informationsfält 4: Objekt associeras.

### <a name="device-class-pima-partial-object-data-get"></a>Hämta partiella objektdata för Enhetsklass

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Ikon** ![ Ikonen Hämta partiella objektdata för Enhetsklass Pima](./media/user-guide/usbx-events/image29.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Pima Partial Object Data Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Offset begärd.
- Informationsfält 4: Begärd längd.

### <a name="device-class-pima-response-send"></a>Skicka Pima-svar för enhetsklass 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Ikon** ![ Ikonen Skicka svar från Device Class Pima](./media/user-guide/usbx-events/image30.png)

**Beskrivning**

Den här händelsen representerar en Pima Response Send-händelse för USBX-enhetsklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Svarskod.
- Informationsfält 3: Nummerparameter.
- Informationsfält 4: Pima-parameter 1.

### <a name="device-class-pima-storage-id-send"></a>Device Class Pima Storage ID Send 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Ikon** ![ Ikonen Skicka enhetsklass-Pima Storage-ID](./media/user-guide/usbx-events/image31.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Pima Storage Id Send Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-pima-storage-info-send"></a>Device Class Pima Storage Info Send 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Ikon** ![ Ikonen Skicka information Storage Pima för enhetsklass](./media/user-guide/usbx-events/image32.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass-Pima Storage Skicka händelse med information.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-activate"></a>Device Class Rndis Activate 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Ikon** ![ Aktiveringsikon för Device Class Rndis](./media/user-guide/usbx-events/image33.png)

**Beskrivning**

Den här händelsen representerar en AKTIVERINGShändelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-deactivate"></a>Inaktivera enhetsklass 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Ikon** ![ Ikon för inaktivera enhetsklass](./media/user-guide/usbx-events/image34.png)

**Beskrivning**

Den här händelsen representerar en inaktiverad händelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-message-keep-alive"></a>Device Class Rndis Message Keep Alive 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**Ikon** ![ Ikonen Device Class Rndis Message Keep Alive](./media/user-guide/usbx-events/image35.png)

**Beskrivning**

Den här händelsen representerar en USBX Device Class Rndis Message Keep Alive-händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-message-query"></a>Meddelandefråga för enhetsklass -Rndis 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Ikon** ![ Ikon för meddelandefråga för enhetsklass -Rndis](./media/user-guide/usbx-events/image36.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass med Rndis-meddelandefrågehändelsen.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Rndis OID.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-message-reset"></a>Meddelandeåterställning för enhetsklass 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Ikon** ![ Ikon för meddelandeåterställning för enhetsklass -Rndis](./media/user-guide/usbx-events/image37.png)

**Beskrivning**

Den här händelsen representerar en Rndis-meddelandeåterställningshändelse för USBX-enhetsklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.

### <a name="device-class-rndis-message-set"></a>Meddelandeuppsättning för enhetsklass 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Ikon** ![ Ikon för enhetsklass-Rndis-meddelandeuppsättning](./media/user-guide/usbx-events/image38.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass med Rndis-meddelandeuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Rndis OID.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-packet-receive"></a>Inkommande device class Rndis-paket 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Ikon** ![ Ikonen Device Class Rndis Packet Receive](./media/user-guide/usbx-events/image39.png)

**Beskrivning**

Den här händelsen representerar en usbx-enhet klass Rndis paket tar emot händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-rndis-packet-transmit"></a>Device Class Rndis-paket överföring 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Ikon** ![ Ikon för enhetsklass-Rndis-paket överföring](./media/user-guide/usbx-events/image40.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass med Rndis-paket överföringshändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-activate"></a>Aktivera Storage enhetsklass 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Ikon** ![ Ikonen Enhetsklass Storage Aktivera](./media/user-guide/usbx-events/image41.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage aktivera händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-deactivate"></a>Inaktivera Storage enhetsklass 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Ikon** ![ Ikon för Storage enhetsklass](./media/user-guide/usbx-events/image42.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage inaktivera händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-format"></a>Device Class Storage Format 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Ikon** ![ Ikonen Device Class Storage Format](./media/user-guide/usbx-events/image43.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage-formathändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-inquiry"></a>Förfrågan om Storage enhetsklass 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Ikon** ![ Ikon för Storage enhetsklassförfrågan](./media/user-guide/usbx-events/image44.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage en förfråganshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-mode-select"></a>Välj Storage enhetklassläge

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Ikon** ![ Ikonen Välj Storage enhetklassläge](./media/user-guide/usbx-events/image45.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage välj händelse i läge.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-mode-sense"></a>Device Class Storage Mode Sense 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Ikon** ![ Ikon för Storage sense i enhetsläge](./media/user-guide/usbx-events/image46.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage sense-händelse i läge.

Informationsfält 

- nfo Fält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-prevent-allow-media-removal"></a>Device Class Storage Förhindra borttagning av media 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Ikon** ![ Ikon för Storage förhindra borttagning av media](./media/user-guide/usbx-events/image47.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage förhindra att media tas bort.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-read"></a>Läsa Storage enhetsklass 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Ikon** ![ Ikonen Device Class Storage Read (Läsa)](./media/user-guide/usbx-events/image48.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage Read-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Sektor.
- Informationsfält 4: Talsektorer.

### <a name="device-class-storage-read-capacity"></a>Kapacitet för Storage läsning 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Ikon** ![ Ikon för Storage läsa kapacitet för enhetsklass](./media/user-guide/usbx-events/image49.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage Read Capacity Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-read-format-capacity"></a>Kapacitet för Storage för enhetsklassläsningsformat 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Ikon** ![ Kapacitetsikonen Storage För enhetsklass och läsformat](./media/user-guide/usbx-events/image50.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage Read Format Capacity Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-read-toc"></a>Device Class Storage Read TOC 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Ikon** ![ Ikon för Storage för enhetsklassläsning](./media/user-guide/usbx-events/image51.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage Läsa TOC-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-request-sense"></a>Device Class Storage Request Sense 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Ikon** ![ Ikonen Device Class Storage Request Sense](./media/user-guide/usbx-events/image52.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage Request Sense Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Avkänningsnyckel.
- Informationsfält 4: Kod.

### <a name="device-class-storage-start-stop"></a>Startstopp Storage enhetsklass 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Ikon** ![ Ikon för Storage start/stopp för enhetsklass](./media/user-guide/usbx-events/image53.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage starta/stoppa-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-test-ready"></a>Device Class Storage Test Ready 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Ikon** ![ Ikon för Storage Test klar för enhetsklass](./media/user-guide/usbx-events/image54.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage testklar händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-verify"></a>Device Class Storage Verify 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Ikon** ![ Ikonen Device Class Storage Verify (Verifiera)](./media/user-guide/usbx-events/image55.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage Verifiera händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-class-storage-write"></a>Device Class Storage Write 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Ikon** ![ Skrivningsikon Storage Device Class](./media/user-guide/usbx-events/image56.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsklass Storage skrivhändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Lun.
- Informationsfält 3: Sektor.
- Informationsfält 4: Talsektorer.

### <a name="device-stack-alternate-setting-get"></a>Alternativ inställning för enhetsstack hämta 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Ikon** ![ Ikonen Hämta alternativ inställning för enhetsstack](./media/user-guide/usbx-events/image57.png)

**Beskrivning**

Den här händelsen representerar en alternativ USBX-enhetsstack med inställningen Hämta händelse.

**Informationsfält**

- Informationsfält 1: Gränssnittsvärde.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-alternate-setting-set"></a>Alternativ inställningsuppsättning för enhetsstack 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Ikon** ![ Ikon för alternativ inställningsuppsättning för enhetsstack](./media/user-guide/usbx-events/image58.png)

**Beskrivning**

Den här händelsen representerar en alternativ inställningsuppsättningshändelse för USBX-enhetsstack.

**Informationsfält**
- Informationsfält 1: Gränssnittsvärde.
- Informationsfält 2: Alternativt inställningsvärde.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-class-register"></a>Enhetsstackklassregister 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Ikon** ![ Ikon för enhetsstackklassregister](./media/user-guide/usbx-events/image59.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackklassregisterhändelse.

**Informationsfält**

- Informationsfält 1: Klassnamn.
- Informationsfält 2: Gränssnittsnummer.
- Informationsfält 3: Parameter.
- Informationsfält 4: Används inte.

### <a name="device-stack-clear-feature"></a>Rensa funktion för enhetsstack 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Ikon** ![ Ikonen Rensa funktion för enhetsstack](./media/user-guide/usbx-events/image60.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstack clear feature-händelse.

**Informationsfält**

- Informationsfält 1: Typ av begäran.
- Informationsfält 2: Begärandevärde. Informationsfält 3: Begärandeindex.
- Informationsfält 4: Används inte.

### <a name="device-stack-configuration-get"></a>Hämta konfiguration av enhetsstack 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Ikon** ![ Ikonen Hämta för konfiguration av enhetsstack](./media/user-guide/usbx-events/image61.png)

**Beskrivning**

Den här händelsen representerar en HÄMTA-händelse för en USBX-enhetsstackkonfiguration.

**Informationsfält** 

- Informationsfält 1: Konfigurationsvärde.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-configuration-set"></a>Konfigurationsuppsättning för enhetsstack 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Ikon** ![ Ikon för konfigurationsuppsättning för enhetsstack](./media/user-guide/usbx-events/image62.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackskonfigurationsuppsättningshändelse.

**Informationsfält** 

- Informationsfält 1: Konfigurationsvärde.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-connect"></a>Enhetsstacks-Anslut 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Ikon** ![ Ikon för Anslut enhetsstack](./media/user-guide/usbx-events/image63.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackbeskrivning för att skicka händelse.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-descriptor-send"></a>Skicka enhetsstacksbeskrivning 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Ikon** ![ Ikonen Skicka i Enhetsstack](./media/user-guide/usbx-events/image64.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackbeskrivning för att skicka händelse.

**Informationsfält**

- Informationsfält 1: Beskrivningstyp.
- Informationsfält 2: Begärandeindex.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-disconnect"></a>Koppla från enhetsstack 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Ikon** ![ Ikon för frånkoppling av enhetsstack](./media/user-guide/usbx-events/image65.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackens frånkopplingshändelse.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-endpoint-stall"></a>Slutpunkten för enhetsstacken har stannat upp 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Ikon** ![ Ikon för slutpunktsstopp för enhetsstack](./media/user-guide/usbx-events/image66.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackslutpunkt som stoppas.

**Informationsfält** 

- Informationsfält 1: Slutpunkt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-get-status"></a>Hämta status för enhetsstack 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Ikon** ![ Ikonen Hämta status för enhetsstack](./media/user-guide/usbx-events/image67.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstack hämta statushändelse.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-host-wakeup"></a>Aktivering av värd för enhetsstack 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Ikon** ![ Aktiveringsikon för värd för enhetsstack](./media/user-guide/usbx-events/image68.png)

**Beskrivning**

Den här händelsen representerar en aktiveringshändelse för en USBX-enhetsstackvärd.

**Informationsfält** 

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-initialize"></a>Initiera enhetsstacken 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Ikon** ![ Ikonen Initiera i enhetsstack](./media/user-guide/usbx-events/image69.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstack som initierar händelsen.

**Informationsfält** 

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-interface-delete"></a>Ta bort gränssnitt för enhetsstack 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Ikon** ![ Ikonen Ta bort gränssnitt för enhetsstack](./media/user-guide/usbx-events/image70.png)

**Beskrivning**

Den här händelsen representerar en usbx-enhetsstackens gränssnitts-borttagningshändelse.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-interface-get"></a>Device Stack Interface Get 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Ikon** ![ Ikonen Hämta i Gränssnittet för enhetsstack](./media/user-guide/usbx-events/image71.png)

**Beskrivning**

Den här händelsen representerar en USBX Device Stack Interface Get-händelse.

**Informationsfält** 

- Informationsfält 1: Gränssnittsvärde.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-interface-set"></a>Gränssnittsuppsättning för enhetsstack 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Ikon** ![ Ikon för Enhetsstack-gränssnittsuppsättning](./media/user-guide/usbx-events/image72.png)

**Beskrivning**

Den här händelsen representerar en USBX Device Stack-gränssnittsuppsättningshändelse.

**Informationsfält** 

- Informationsfält 1: Begärandevärde. Informationsfält 2: Begärandeindex.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-set-feature"></a>Set-funktion för enhetsstack 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Ikon** ![ Ikon för enhetsstackuppsättningsfunktion](./media/user-guide/usbx-events/image73.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstackuppsättningsfunktionshändelse.

**Informationsfält** 

- Informationsfält 1: Begärandevärde. Informationsfält 2: Begärandeindex.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-transfer-abort"></a>Avbryt överföring av enhetsstack 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Ikon** ![ Ikonen Avbryt överföring av enhetsstack](./media/user-guide/usbx-events/image74.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstacköverföringshändelse som avbryts.

**Informationsfält** 

- Informationsfält 1: Överföringsbegäran.
- Informationsfält 2: Slutförandekod.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-transfer-all-request-abort"></a>Överföring av enhetsstack – alla förfrågningar avbryts 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Ikon** ![ Ikonen Överför alla förfrågningar om överföring av enhetsstack](./media/user-guide/usbx-events/image75.png)

**Beskrivning**

Den här händelsen representerar en USBX-enhetsstack som överför alla avbrottshändelse för begäran.

**Informationsfält** 

- Informationsfält 1: Slutpunkt.
- Informationsfält 2: Slutförandekod.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="device-stack-transfer-request"></a>Begäran om överföring av enhetsstack 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Ikon** ![ Ikonen Överföringsbegäran för enhetsstack](./media/user-guide/usbx-events/image76.png)

**Beskrivning**

Den här händelsen representerar en överföringsbegärandehändelse för USBX-enhetsstack.

**Informationsfält**

- Informationsfält 1: Överföringsbegäran.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-asix-activate"></a>Aktivera värdklass somix 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Ikon** ![ Aktiveringsikon för värdklass somix](./media/user-guide/usbx-events/image77.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för aktivering av Asix.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-asix-deactivate"></a>Inaktivera värdklass somix 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Ikon** ![ Ikon för inaktivera värdklass som asix](./media/user-guide/usbx-events/image78.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass– asix-inaktiveringshändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-asix-interrupt-notification"></a>Meddelande om avbrott i värdklassen Asix 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Ikon** ![ Meddelandeikon för avbrottsmeddelande för värdklass asix](./media/user-guide/usbx-events/image79.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Asix Interrupt Notification Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-asix-read"></a>Läsa värdklass som asix 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Ikon** ![ Ikon för att läsa värdklass somix](./media/user-guide/usbx-events/image80.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass– asixläsningshändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Datapekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-asix-write"></a>Host Class Asix Write 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Ikon** ![ Skrivikon för värdklass somix](./media/user-guide/usbx-events/image81.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass – asix-skrivningshändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Datapekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-activate"></a>Aktivera värdklassljud 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Ikon** ![ Aktiveringsikon för värdklassljud](./media/user-guide/usbx-events/image82.png)

**Beskrivning**

Den här händelsen representerar en LJUDaktivera händelse för USBX-värdklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-control-value-get"></a>Host Class Audio Control Value Get 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Ikon** ![ Ikonen Hämta värde för värdklassljudkontroll](./media/user-guide/usbx-events/image83.png)

**Beskrivning**

Den här händelsen representerar ett LJUDKONTROLLvärde för USBX-värdklass Hämta händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-control-value-set"></a>Värdeuppsättning för ljudkontroll för värdklass 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Ikon** ![ Ikon för värdeuppsättning för värdklassljudkontroll](./media/user-guide/usbx-events/image84.png)

**Beskrivning**

Den här händelsen representerar en intern uppskjuten bearbetningshändelse för NetX I/O-drivrutinen.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Infofält 2: Ljudkontroll.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-deactivate"></a>Inaktivera värdklassljud 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Ikon** ![ Inaktivera ikon för värdklassljud](./media/user-guide/usbx-events/image85.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass – Inaktivera ljudhändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-read"></a>Ljudläsning för värdklass 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Ikon** ![ Ikon för ljudläsning för värdklass](./media/user-guide/usbx-events/image86.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för ljudläsningshändelse.

- Informationsfält 
- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-streaming-sampling-get"></a>Hämta sampling av ljudströmning för värdklass 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Ikon** ![ Hämta ikon för sampling av ljudströmning för värdklass](./media/user-guide/usbx-events/image87.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass – Hämta händelse för ljudströmningssampling.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-streaming-sampling-set"></a>Samplingsuppsättning för ljudströmning för värdklass 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Ikon** ![ Ikon för insamlingsuppsättning för ljudströmning för värdklass](./media/user-guide/usbx-events/image88.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för samplingsuppsättningshändelse för ljudströmning.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Ljudsampling.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-audio-write"></a>Ljudskrivning för värdklass 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Ikon** ![ Ikon för ljudskrivning för värdklass](./media/user-guide/usbx-events/image89.png)

**Beskrivning**

Den här händelsen representerar en ljudskrivningshändelse för USBX-värdklass.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-activate"></a>Aktivera Cdc Acm för värdklass 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Ikon** ![ Aktiveringsikon för värdklass C D C A C M](./media/user-guide/usbx-events/image90.png)

**Beskrivning**

Den här händelsen representerar en AKTIVERINGShändelse för USBX-värdklassen Cdc Acm.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-deactivate"></a>Inaktivera Cdc Acm för värdklass 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Ikon** ![ Ikon för inaktiverad värdklass C D C A C M](./media/user-guide/usbx-events/image91.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass cdc Acm inaktivera händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Host Class Cdc Acm Ioctl Abort In Pipe 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Ikon** ![ Ikonen Avbryt i pipe för värdklass C D C A C M I O C T L Avbryt i pipe](./media/user-guide/usbx-events/image92.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Abort In Pipe Event.

Informationsfält 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Host Class Cdc Acm Ioctl Abort Out Pipe 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Ikon** ! [[Ikon för att avbryta pipe för värdklass C D C A C](./media/user-guide/usbx-events/image93.png) M I O C T L

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Abort Out Pipe Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Host Class Cdc Acm Ioctl Get Device Status 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Ikon** ![ Ikon för att hämta enhetsstatus för värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image94.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Hämta enhetsstatushändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Enhetsstatus.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Host Class Cdc Acm Ioctl Get Line Coding 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Ikon** ![ Ikon för att hämta linjekodning för värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image95.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Get Line Coding Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Återanrop av meddelanden för Host Class Cdc Acm Ioctl

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Ikon** ![ Ikon för återanrop av meddelanden från värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image96.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Notification Callback Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Skicka break för Cdc Acm Ioctl för värdklass 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Ikon** ![ Skicka brytikon för Värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image97.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Send Break Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Kodning av radkodning för Cdc Acm Ioctl för värdklass 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Ikon** ![ Ikon för ange radkodningsikon för värdklass C D C A C M I O C T L ange ](./media/user-guide/usbx-events/image97.png) radkodning](./media/user-guide/usbx-events/image98.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Set Line Coding Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Värdklass Cdc Acm Ioctl Ange radtillstånd 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Ikon** ![ Ikon för ange radtillstånd för värdklass C D C A C M I O C T L](./media/user-guide/usbx-events/image99.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Cdc Acm Ioctl Set Line State Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-read"></a>Läsa Cdc Acm för värdklass 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Ikon** ![ Läsikon för Värdklass C D C A C M](./media/user-guide/usbx-events/image100.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass cdc Acm läshändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-reception-start"></a>Host Class Cdc Acm Mottagningsstart 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Ikon** ![ Startikon för värdklass C D C A C M-mottagning](./media/user-guide/usbx-events/image101.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass cdc Acm mottagning starthändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-reception-stop"></a>Host Class Cdc Acm– mottagningsstopp 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Ikon** ![ Ikon för stopp av mottagning i värdklass C D C A C M](./media/user-guide/usbx-events/image102.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass cdc Acm mottagningsstopp händelse.

**Informationsfält**

- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-cdc-acm-write"></a>Host Class Cdc Acm Write 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Ikon** ![ Skrivikon för Värdklass C D C A C M](./media/user-guide/usbx-events/image103.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass cdc Acm skrivhändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-dpump-activate"></a>Aktivera värdklass-Dpump 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Ikon** ![ Aktiveringsikon för värdklass-Dpump](./media/user-guide/usbx-events/image104.png)

**Beskrivning**

Den här händelsen representerar en aktiveringshändelse för USBX-värdklass Dpump.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-dpump-deactivate"></a>Inaktivera värdklass-Dpump 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Ikon** ![ Ikon för inaktiverad värdklass-Dpump](./media/user-guide/usbx-events/image105.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Dpump Inaktivera händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-dpump-read"></a>Läsa värdklass-Dpump 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Ikon** ![ Ikonen Läsa för värdklass-Dpump](./media/user-guide/usbx-events/image106.png)

**Beskrivning**

Den här händelsen representerar en LÄShändelse för USBX-värdklass Dpump.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-dpump-write"></a>Skriv för värdklass-Dpump 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Ikon** ![ Skrivikon för värdklass-Dpump](./media/user-guide/usbx-events/image107.png)

**Beskrivning**

Den här händelsen representerar en skrivningshändelse för USBX-värdklass Dpump.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-activate"></a>Hid-aktivering för värdklass 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Ikon** ![ Ikon för hid-aktivering för värdklass](./media/user-guide/usbx-events/image108.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för hid-aktiveringshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-client-register"></a>Hid-klientregister för värdklass 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Ikon** ![ Ikon för hid-klientregister för värdklass](./media/user-guide/usbx-events/image109.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass, Hid Client Register Event.

**Informationsfält** 

- Informationsfält 1: Hid-klientnamn.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-deactivate"></a>Inaktivera värdklass 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Ikon** ![ Ikon för inaktiverad värdklass](./media/user-guide/usbx-events/image110.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för inaktiverad händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-idle-get"></a>Hid Idle Get för värdklass 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Ikon** ![ Ikonen Hid Idle Get (Hämta) för värdklass hid inaktiv](./media/user-guide/usbx-events/image111.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass, Hid Idle Get Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-idle-set"></a>Hid Idle Set för värdklass 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Ikon** ![ Ikon för Hid Idle Set för värdklass](./media/user-guide/usbx-events/image112.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass, Hid Idle Set Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-keyboard-activate"></a>Aktivera hid-tangentbord för värdklass 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Ikon** ![ Aktiveringsikon för värdklassens hid-tangentbord](./media/user-guide/usbx-events/image113.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Aktiveringshändelse för hid-tangentbord.

**Informationsfält**
<p>Informationsfält 1: Klassinstans.
<p>Informationsfält 2: Hid-klientinstans.
<p>Informationsfält 3: Används inte.
<p>Informationsfält 4: Används inte.

### <a name="host-class-hid-keyboard-deactivate"></a>Inaktivera hid-tangentbord för värdklass 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Ikon** ![ Inaktivera tangentbordsikon för värdklass hid](./media/user-guide/usbx-events/image114.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Inaktivera tangentbord med hid-tangentbord.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Hid-klientinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-mouse-activate"></a>Aktivera hid mus för värdklass 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Ikon** ![ Aktiveringsikon för värdklass hid mus](./media/user-guide/usbx-events/image115.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass För musaktiverad händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Hid-klientinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-mouse-deactivate"></a>Inaktivera mus för värdklass 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Ikon** ![ Ikon för inaktiverad mus för värdklass](./media/user-guide/usbx-events/image116.png)

**Beskrivning**

- Den här händelsen representerar en USBX-värdklass inaktiverad mushändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Hid-klientinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-remote-control-activate"></a>Aktivera fjärrstyrning av värdklass hid 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Ikon** ![ Aktiveringsikon för värdklass hid-fjärrstyrning](./media/user-guide/usbx-events/image117.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass, Hid Remote Control Activate Event.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Hid-klientinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-remote-control-deactivate"></a>Inaktivera fjärrstyrning av värdklass 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Ikon** ![ Ikon för inaktiverad fjärrstyrning i värdklass](./media/user-guide/usbx-events/image118.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass inaktiverad fjärrstyrningshändelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Hid-klientinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-report-get"></a>Hämta hid-rapport för värdklass 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Ikon** ![ Ikonen Hämta för värdklass hid-rapport](./media/user-guide/usbx-events/image119.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass, Hid Report Get.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Klientrapport.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hid-report-set"></a>Hid-rapportuppsättning för värdklass 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Ikon** ![ Ikon för Hid Report Set för värdklass](./media/user-guide/usbx-events/image120.png)

**Beskrivning** Den här händelsen representerar en USBX-värdklass hid-rapportuppsättning.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Klientrapport.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-activate"></a>Aktivera värdklasshubb 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Ikon** ![ Aktiveringsikon för värdklasshubb](./media/user-guide/usbx-events/image121.png)

**Beskrivning**

Den här händelsen representerar en aktiveringshändelse för en USBX-värdklasshubb.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-change-detect"></a>Identifiering av ändring av värdklasshubb 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Ikon** ![ Ikon för ändring av identifiering av värdklasshubb](./media/user-guide/usbx-events/image122.png)

**Beskrivning**

Den här händelsen representerar en ÄNDRINGshändelse för EN USBX-värdklasshubb.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-deactivate"></a>Inaktivera värdklasshubb 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**Ikon** ![ Inaktivera ikon för värdklasshubb](./media/user-guide/usbx-events/image123.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklasshubb för inaktiveringshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-port-change-connection-process"></a>Ändringsanslutningsprocess för värdklasshubbport 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Ikon** ![ Ikonen Ändra anslutningsprocess för värdklasshubbport](./media/user-guide/usbx-events/image124.png)

**Beskrivning**

Den här händelsen representerar en ändringsprocess för portanslutningen för en USBX-värdklasshubb.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Port.
- Informationsfält 3: Portstatus.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-port-change-enable-process"></a>Aktivera process för portändring för värdklasshubb 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Ikon** ![ Ikonen Aktivera process för portändring för värdklasshubb](./media/user-guide/usbx-events/image125.png)

**Beskrivning**

Den här händelsen representerar en portändringsprocess för USBX-värdklasshubb för att aktivera processhändelsen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Port.
- Informationsfält 3: Portstatus.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-port-change-over-current-process"></a>Portändring för värdklasshubb över aktuell process 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Ikon** ![ Ikon för portändring för värdklasshubb över aktuell process](./media/user-guide/usbx-events/image126.png)

**Beskrivning**

Den här händelsen representerar allokering av ett paket via nx_packet_allocate.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Port.
- Informationsfält 3: Portstatus.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-port-change-reset-process"></a>Process för ändringsåterställning av värdklasshubbport 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Ikon** ![ Ikon för ändring av återställningsprocess för värdklasshubbport](./media/user-guide/usbx-events/image127.png)

**Beskrivning**

Den här händelsen representerar en HÄNDELSE för ändringsåterställning av port för USBX-värdklasshubb.

**Informationsfält**

- Informationsfält 1: Hubb. Informationsfält 2: Port.
- Informationsfält 3: Portstatus.
- Informationsfält 4: Används inte.

### <a name="host-class-hub-port-change-suspend-process"></a>Pausprocess för portändring för värdklasshubb 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Ikon** ![ Ikon för ändring av pausprocess för värdklasshubbport](./media/user-guide/usbx-events/image128.png)

**Beskrivning**

Den här händelsen representerar en usbx-värdklasshubb, portändring, pausprocesshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Port.
- Informationsfält 3: Portstatus.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-activate"></a>Aktivera Pima för värdklass 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Ikon** ![ Aktiveringsikon för värdklass-Pima](./media/user-guide/usbx-events/image129.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för aktiveringshändelsen i Pima.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-deactivate"></a>Inaktivera Pima för värdklass 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Ikon** ![ Ikon för att inaktivera värdklass-Pima](./media/user-guide/usbx-events/image130.png)

**Beskrivning**

Den här händelsen representerar en Pima-inaktiveringshändelse i USBX-värdklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-device-info-get"></a>Information om värdklass för Pima-enhet hämta 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Ikon** ![ Ikonen Hämta information om värdklassenhetsinformation för värdklass](./media/user-guide/usbx-events/image131.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Pima Device Info Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Pima-enhet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-device-reset"></a>Återställning av värdklass för Pima-enhet 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Ikon** ![ Ikon för återställning av värdklassenhet](./media/user-guide/usbx-events/image132.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklasshändelse för återställning av enhet.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-notification"></a>Pima-meddelande för värdklass 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Ikon** ![ Meddelandeikon för värdklass-Pima](./media/user-guide/usbx-events/image133.png)

**Beskrivning**

Den här händelsen representerar en Pima-meddelandehändelse för EN USBX-värdklass.

**Informationsfält**

- Informationsfält 1: Klassinstans. Informationsfält 2: Händelsekod.
- Informationsfält 3: Transaktions-ID.
- Informationsfält 4: Parameter1.

### <a name="host-class-pima-number-objects-get"></a>Host Class Pima Number Objects Get 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Ikon** ![ Pima Number Objects Get-ikon för värdklass](./media/user-guide/usbx-events/image134.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Pima Number Objects Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-close"></a>Stäng Pima-objekt för värdklass 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Ikon** ![ Stängningsikon för värdklass-Pima-objekt](./media/user-guide/usbx-events/image135.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Close-händelse i USBX-värdklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-copy"></a>Pima-objektkopiering för värdklass 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Ikon** ![ Pima Object Copy-ikon för värdklass](./media/user-guide/usbx-events/image136.png)

**Beskrivning**

Den här händelsen representerar en Pima-objektkopieringshändelse för USBX-värdklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-delete"></a>Ta bort Pima-objekt för värdklass 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Ikon** ![ Ikonen Ta bort objekt för värdklass Pima](./media/user-guide/usbx-events/image137.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för borttagning av objekt i Pima-klassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-get"></a>Host Class Pima Object Get 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Ikon** ![ Pima Object Get-ikon för värdklass](./media/user-guide/usbx-events/image138.png)

**Beskrivning**

Den här händelsen representerar att hämta RARP-information via nx_rarp_info_get.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Objekt.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-info-get"></a>Information om Pima-objekt för värdklass get 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Ikon** ![ Pima Object Info Hämta-ikon för värdklass](./media/user-guide/usbx-events/image139.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för Pima Object Info Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Objekt.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-info-send"></a>Skicka information om Pima-objekt för värdklass 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Ikon** ![ Skicka ikon för Pima-objektinformation för värdklass](./media/user-guide/usbx-events/image140.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för Pima Object Info Send Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-move"></a>Flytta Pima-objekt för värdklass 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikon** ![ Flytta objektikon för värdklass Pima](./media/user-guide/usbx-events/image141.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för Pima Object Move Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Objekt.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-object-send"></a>Skicka Pima-objekt för värdklass 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikon** ![ Ikonen Skicka Pima-objekt för värdklass](./media/user-guide/usbx-events/image142.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Send-händelse för EN USBX-värdklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekt.
- Informationsfält 3: Objektbuffert.
- Informationsfält 4: Objektlängd.

### <a name="host-class-pima-object-transfer-abort"></a>Avbryt överföring av objekt i värdklassens Pima-objekt 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Ikon** ![ Ikonen För att avbryta överföring av värdklassobjekt i Pima-klass](./media/user-guide/usbx-events/image143.png)

**Beskrivning**

Den här händelsen representerar en Pima Object Transfer Abort-händelse i USBX-värdklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Objekt.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-read"></a>Pima Read för värdklass 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Ikon** ![ Pima Read-ikon för värdklass](./media/user-guide/usbx-events/image144.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för Pima Read-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Datapekare.
- Infofält 3: Datalängd.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-request-cancel"></a>Avbryt begäran om Pima för värdklass 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Ikon** ![ Ikonen För att avbryta begäran för värdklass Pima](./media/user-guide/usbx-events/image145.png)

**Beskrivning**

Den här händelsen representerar en Pima Request Cancel-händelse för USBX-värdklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-session-close"></a>Pima-session för värdklass stäng 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Ikon** ![ Ikon för Pima-sessionsslut för värdklass](./media/user-guide/usbx-events/image146.png)

**Beskrivning**

Den här händelsen representerar en Pima Session Close-händelse för EN USBX-värdklass.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Pima-session.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-session-open"></a>Värdklassens Pima-session är öppen 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Ikon** ![ Ikon för att öppna värdklass-Pima-session](./media/user-guide/usbx-events/image147.png)

**Beskrivning** Den här händelsen representerar en Pima Session Open-händelse för USBX-värdklassen.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Pima-session.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-storage-ids-get"></a>Hämta Pima-Storage-ID:n för värdklass 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Ikon** ![ Ikonen Hämta för värdklass-Pima Storage-ID:n](./media/user-guide/usbx-events/image148.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Pima Storage Ids Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- nfo Fält 2: Storage ID-matris.
- Informationsfält 3: Storage ID-längd.
Informationsfält 4: Används inte.

### <a name="host-class-pima-storage-info-get"></a>Host Class Pima Storage Info Get 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Ikon** ![ Ikon för att hämta Storage Pima för värdklass](./media/user-guide/usbx-events/image149.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Pima Storage Info Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Storage-ID.
- Informationsfält 3: Storage.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-thumb-get"></a>Pima Thumb Get för värdklass 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikon** ![ Pima Thumb Get-ikon för värdklass](./media/user-guide/usbx-events/image150.png)

**Beskrivning**

Den här händelsen representerar att en TCP-serveranslutning inte kan nås via nx_tcp_server_socket_unaccept.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Objekthandtag.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-pima-write"></a>Host Class Pima Write 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikon** ![ Ikon för Pima-skrivning för värdklass](./media/user-guide/usbx-events/image151.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Pima Write.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Datalängd.
- Informationsfält 4: Används inte.

### <a name="host-class-printer-activate"></a>Aktivera värdklassskrivare 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Ikon** ![ Aktiveringsikon för värdklassskrivare](./media/user-guide/usbx-events/image152.png)

**Beskrivning**

Den här händelsen representerar en aktiveringshändelse för USBX-värdklassskrivare.

**Informationsfält**

- Informationsfält 1: Pekare till IP-instans.
- Informationsfält 2: Pekare till socket.
- Informationsfält 3: Typ av tjänst.
- Informationsfält 4: Ta emot fönsterstorlek.

### <a name="host-class-printer-deactivate"></a>Inaktivera värdklassskrivare 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Ikon** ![ Inaktivera ikon för värdklassskrivare](./media/user-guide/usbx-events/image153.png)

**Beskrivning**

Den här händelsen representerar en inaktiverad USBX-värdklassskrivare.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-printer-name-get"></a>Host Class Printer Name Get 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Ikon** ![ Ikonen Hämta namn på värdklassskrivare](./media/user-guide/usbx-events/image154.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för skrivarnamn get-händelse.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-printer-read"></a>Läsa värdklassskrivare 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Ikon** ![ Ikon för skrivarläsning för värdklass](./media/user-guide/usbx-events/image155.png)

**Beskrivning**

Den här händelsen representerar en LÄShändelse för USBX-värdklassskrivare.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-printer-soft-reset"></a>Mjuk återställning av värdklassskrivare 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Ikon** ![ Ikon för mjuk återställning av värdklassskrivare](./media/user-guide/usbx-events/image156.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklassskrivare för mjuk återställning.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-printer-status-get"></a>Hämta status för värdklassskrivare 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Ikon** ![ Ikonen Hämta status för värdklassskrivare](./media/user-guide/usbx-events/image157.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Skrivarstatus Hämta händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Skrivarstatus.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-printer-write"></a>Skriva värdklassskrivare 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Ikon** ![ Skrivikon för värdklassskrivare](./media/user-guide/usbx-events/image158.png)

**Beskrivning**

Den här händelsen representerar skrivning av en USBX-värdklassskrivare.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Datapekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-activate"></a>Aktivering av värdklass prolific 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Ikon** ![ Aktiveringsikon för värdklass](./media/user-guide/usbx-events/image159.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklasshändelse för aktivering av program.

**Informationsfält** 

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-deactivate"></a>Inaktivera värdklass prolific 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Ikon** ![ Ikon för inaktivera värdklass](./media/user-guide/usbx-events/image160.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklassinaktiveringshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Avbryt prolific Ioctl för värdklass i pipe 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Ikon** ![ Host Class Prolific I O C T L Abort In Pipe-ikon](./media/user-guide/usbx-events/image161.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific Ioctl Abort In Pipe Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Värdklass prolific Ioctl Abort Out Pipe 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Ikon** ![ Ikon för värdklassprolific I O C T L Abort Out Pipe](./media/user-guide/usbx-events/image162.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific Ioctl Abort Out Pipe Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-get-device-status"></a>Hämta enhetsstatus för värdklass prolific Ioctl 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Ikon** ![ Ikon för att hämta enhetsstatus för värdklassprolific I O C T L](./media/user-guide/usbx-events/image163.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific Ioctl Hämta enhetsstatushändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Enhetsstatus.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Host Class Prolific Ioctl Get Line Coding 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Ikon** ![ Ikon för att hämta linjekodning för värdklassprolific I O C T L Get Line](./media/user-guide/usbx-events/image164.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific Ioctl Get Line Coding Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-purge"></a>Rensning av värdklass prolific Ioctl 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Ikon** ![ Ikon för rensning av värdklass prolific Ioctl](./media/user-guide/usbx-events/image165.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific Ioctl Purge Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-report-device"></a>Rapportenhet för värdklass prolific Ioctl 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Ikon** ![ Ikon för rapportenhet för värdklassprolific I O C T L Report](./media/user-guide/usbx-events/image166.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Prolific Ioctl Report Device Status Change Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-send-break"></a>Skicka bryt om värdklass prolific Ioctl 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Ikon** ![ Skicka brytikon för värdklassprolific I O C T L](./media/user-guide/usbx-events/image167.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific Ioctl Send Break Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Kodning av radkodning för värdklassprolific Ioctl Set 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Ikon** ![ Kodningsikon för värdklassprolific I O C T L Set Line Coding](./media/user-guide/usbx-events/image168.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för kodningshändelsen Prolific Ioctl Set Line Coding.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-ioctl-set-line-state"></a>Radtillstånd för värdklassprolific Ioctl Set 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Ikon** ![ Ikon för ange radtillstånd för värdklassprolific I O C T L](./media/user-guide/usbx-events/image169.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklasss prolific Ioctl Set Line State-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Parameter.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-read"></a>Läsa värdklass 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Ikon** ![ Ikon för värdklassläsning](./media/user-guide/usbx-events/image170.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass prolific read-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-reception-start"></a>Start av mottagning av värdklass 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Ikon** ![ Startikon för värdklassmottagande](./media/user-guide/usbx-events/image171.png)

**Beskrivning**

Den här händelsen representerar en START-händelse för USBX-värdklass för mottagningsstart.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-reception-stop"></a>Mottagningsstopp för värdklass 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**Ikon** ![ Stoppikon för värdklassmottagande](./media/user-guide/usbx-events/image172.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass för mottagningsstopp.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-prolific-write"></a>Skrivning av värdklass 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Ikon** ![ Ikon för skrivning av värdklass](./media/user-guide/usbx-events/image173.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass skrivhändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Data pekare.
- Informationsfält 3: Begärd längd.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-activate"></a>Aktivera Storage värdklass 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Ikon** ![ Ikonen Aktivera Storage värdklass](./media/user-guide/usbx-events/image174.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage aktivera händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-deactivate"></a>Inaktivera Storage värdklass 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Ikon** ![ Ikon för Storage inaktivera värdklass](./media/user-guide/usbx-events/image175.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage inaktivera händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-media-capacity-get"></a>Hämta kapacitet Storage värdklass 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Ikon** ![ Ikonen Hämta Storage värdklassmediakapacitet](./media/user-guide/usbx-events/image176.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage Media Capacity Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-media-format-capacity-get"></a>Host Class Storage Media Format Capacity Get

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Ikon** ![ Hämta-Storage för värdklass i Media Format-kapacitet](./media/user-guide/usbx-events/image177.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage Media Format Capacity Get Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

#### <a name="host-class-storage-media-mount"></a>Värdklass för Storage Media Mount 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Ikon** ![ Ikon för Storage mediamontering för värdklass](./media/user-guide/usbx-events/image178.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage Media Mount-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Sektor.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-media-open"></a>Värdklass Storage Media Open 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Ikon** ![ Ikonen Storage Media Open för värdklass](./media/user-guide/usbx-events/image179.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage Media Open Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Media.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-media-read"></a>Läsa värdklass Storage media 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Ikon** ![ Ikon för Storage medieläsning för värdklass](./media/user-guide/usbx-events/image180.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage medialäsningshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Sektorstart.
- Informationsfält 3: Sektorantal.
- Informationsfält 4: Datapekare.

### <a name="host-class-storage-media-write"></a>Host Class Storage Media Write 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Ikon** ![ Ikon för Storage medieskrivning för värdklass](./media/user-guide/usbx-events/image181.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage mediaskrivningshändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Sektorstart.
- Informationsfält 3: Sektorantal.
- Informationsfält 4: Datapekare.

### <a name="host-class-storage-request-sense"></a>Host Class Storage Request Sense 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Ikon** ![ Ikon för Storage Begär sense för värdklass](./media/user-guide/usbx-events/image182.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage Request Sense Event.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-start-stop"></a>Start/stopp Storage värdklass 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Ikon** ![ Ikon för Storage starta/stoppa för värdklass](./media/user-guide/usbx-events/image183.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage start/stopp-händelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Starta stoppsignal.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-class-storage-unit-ready-test"></a>Test av Storage värdklassenhet 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Ikon** ![ Ikon för Storage för redo Storage för värdklass](./media/user-guide/usbx-events/image184.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdklass Storage enhetsklar testhändelse.

**Informationsfält**

- Informationsfält 1: Klassinstans.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-class-instance-create"></a>Skapa värdstacksklassinstans 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikon** ![ Skapa ikon för värdstackklassinstans](./media/user-guide/usbx-events/image185.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackklassinstans för att skapa händelse.

**Informationsfält**

- Informationsfält 1: Klass.
- Informationsfält 2: Klassinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-class-instance-destroy"></a>Förstöra värdstackklassinstans 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikon** ![ Ta bort ikon för värdstackklassinstans](./media/user-guide/usbx-events/image186.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackklassinstans för destroy-händelse.

**Informationsfält**

- Informationsfält 1: Klass.
- Informationsfält 2: Klassinstans.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-configuration-delete"></a>Ta bort konfiguration av värdstack 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Ikon** ![ Ikonen Ta bort värdstackkonfiguration](./media/user-guide/usbx-events/image187.png)

**Beskrivning**

Den här händelsen representerar en borttagningshändelse för USBX-värdstackens konfiguration.

**Informationsfält**

- Informationsfält 1: Konfiguration.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-configuration-enumerate"></a>Konfigurationsuppräkning för värdstack 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Ikon** ![ Ikon för konfigurationsuppräkning av värdstack](./media/user-guide/usbx-events/image188.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackkonfigurationsuppräkningshändelse.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="stack-configuration-instance-create"></a>Skapa stackkonfigurationsinstans 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Ikon** ![ Ikonen Skapa för Stack-konfigurationsinstans](./media/user-guide/usbx-events/image189.png)

**Beskrivning**

Den här händelsen representerar en SKAPA-händelse för en USBX-värdstackkonfigurationsinstans.

**Informationsfält**

- Informationsfält 1: Konfiguration.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-configuration-instance-delete"></a>Ta bort konfigurationsinstans för värdstack 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Ikon** ![ Ikonen Ta bort konfigurationsinstans för värdstack](./media/user-guide/usbx-events/image190.png)

**Beskrivning**

Den här händelsen representerar en borttagningshändelse för en USBX-värdstackkonfigurationsinstans.

**Informationsfält**

- Informationsfält 1: Konfiguration.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-configuration-set"></a>Konfigurationsuppsättning för värdstack 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Ikon** ![ Ikon för konfigurationsuppsättning för värdstack](./media/user-guide/usbx-events/image191.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstacks konfigurationsuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Konfiguration.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-device-address-set"></a>Enhetsadressuppsättning för värdstack 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Ikon** ![ Ikon för enhetsadressuppsättning för värdstack](./media/user-guide/usbx-events/image192.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackens enhetsadressuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Enhetsadress.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-device-configuration-get"></a>Hämta enhetskonfiguration för värdstack 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Ikon** ![ Ikonen Hämta för enhetskonfiguration för värdstack](./media/user-guide/usbx-events/image193.png)

**Beskrivning**

Den här händelsen representerar en HÄMTA-händelse för en USBX-värdstackenhetskonfiguration.

**Informationsfält**

- Informationsfält 1: Enhet.
- nfo Fält 2: Konfiguration.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-device-configuration-select"></a>Välj enhetskonfiguration för värdstack 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Ikon** ![ Ikonen Välj enhetskonfiguration för värdstack](./media/user-guide/usbx-events/image194.png)

**Beskrivning**

Den här händelsen representerar en ENHETSkonfigurationshändelse för USBX-värdstack.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Konfiguration.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-device-descriptor-read"></a>Läsa enhetsbeskrivning för värdstack 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Ikon** ![ Ikon för Enhetsbeskrivning för värdstack](./media/user-guide/usbx-events/image195.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackenhetsbeskrivningsläsningshändelse.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-device-get"></a>Hämta värdstackenhet 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Ikon** ![ Ikonen Hämta för värdstacksenhet](./media/user-guide/usbx-events/image196.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackenhets get-händelse.

**Informationsfält**

- Informationsfält 1: Enhetsindex.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-device-remove"></a>Ta bort värdstacksenhet 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Ikon** ![ Ikonen Ta bort värdstacksenhet](./media/user-guide/usbx-events/image197.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstack för borttagning av enhet.

**Informationsfält**

- Informationsfält 1: Hcd.
- Informationsfält 2: Överordnad.
- Informationsfält 3: Portindex.
- Informationsfält 4: Enhet.

### <a name="host-stack-device-resource-free"></a>Resurs kostnadsfri för värdstackenhet 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Ikon** ![ Ikon för kostnadsfri resurs för värdstackenhet](./media/user-guide/usbx-events/image198.png)

**Beskrivning**

Den här händelsen representerar en kostnadsfri USBX-värdstackenhetsresurs.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-endpoint-instance-create"></a>Skapa slutpunktsinstans för värdstack 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Ikon** ![ Ikonen Skapa slutpunktsinstans för värdstack](./media/user-guide/usbx-events/image199.png)

**Beskrivning**

Den här händelsen representerar en SKAPA-händelse för en USBX-värdstackslutpunktsinstans.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-endpoint-instance-delete"></a>Ta bort slutpunktsinstans för värdstack 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Ikon** ![ Ikonen Ta bort slutpunktsinstans för värdstack](./media/user-guide/usbx-events/image200.png)

**Beskrivning**

Den här händelsen representerar en borttagningshändelse för en USBX-värdstackslutpunktsinstans.

**Informationsfält**

- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-endpoint-reset"></a>Slutpunktsåterställning för värdstack 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Ikon** ![ Ikon för slutpunktsåterställning för värdstack](./media/user-guide/usbx-events/image201.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstackens slutpunktsåterställningshändelse.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-endpoint-transfer-abort"></a>Migrering av slutpunktsöverföring för värdstack 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Ikon** ![ Ikonen Avbryt avslutsöverföring av värdstack](./media/user-guide/usbx-events/image202.png)

**Beskrivning**

Den här händelsen representerar en avbrottshändelse för en USBX-värdstacks slutpunktsöverföring.

**Informationsfält**

- Informationsfält 1: Slutpunkt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-host-controller-register"></a>Värdstack värdstyrenhetsregister 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Ikon** ![ Registerikon för värdstackvärdstyrenhet](./media/user-guide/usbx-events/image203.png)

**Beskrivning**

Den här händelsen representerar ett USBX-värdstackvärdstyrenhetsregister.

**Informationsfält**

- Informationsfält 1: Hcd-namn.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-initialize"></a>Initiera värdstack 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Ikon** ![ Initieringsikon för värdstack](./media/user-guide/usbx-events/image204.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstack som initierar händelsen.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-interface-endpoint-get"></a>Hämta gränssnittsslutpunkt för värdstack 

#### <a name="interface_-tcp-retry-entry"></a>Interface_ TCP-återförsökspost

**Ikon** ![ Ikonen Hämta för gränssnittsslutpunkt för värdstack](./media/user-guide/usbx-events/image205.png)

**Beskrivning**

Den här händelsen representerar en intern NetX TCP-återförsökshändelse.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Slutpunktsindex.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-interface-instance-create"></a>Skapa gränssnittsinstans för värdstack 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Ikon** ![ Ikonen Skapa gränssnittsinstans för värdstack](./media/user-guide/usbx-events/image206.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstack-gränssnittsinstans för att skapa händelse.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-interface-instance-delete"></a>Ta bort gränssnittsinstans för värdstack 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Ikon** ![ Ta bort ikon för gränssnittsinstans för värdstack](./media/user-guide/usbx-events/image207.png)

**Beskrivning**

Den här händelsen representerar en borttagningshändelse för en USBX-värdstack-gränssnittsinstans.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-interface-set"></a>Gränssnittsuppsättning för värdstack 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Ikon** ![ Ikon för gränssnittsuppsättning för värdstack](./media/user-guide/usbx-events/image208.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstack-gränssnittsuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-interface-setting-select"></a>Gränssnittsinställning för värdstack väljer du 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Ikon** ![ Gränssnittsinställning för värdstack välj ikon](./media/user-guide/usbx-events/image209.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstacks gränssnittsinställning Välj händelse.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-new-configuration-create"></a>Skapa ny konfiguration för värdstack 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Ikon** ![ Ikonen Skapa ny konfiguration för värdstack](./media/user-guide/usbx-events/image210.png)

**Beskrivning**
 
Den här händelsen representerar en USBX-värdstack ny händelse för att skapa konfiguration.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Konfiguration.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-new-device-create"></a>Skapa ny enhet för värdstack 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Ikon** ![ Ikonen Skapa ny enhet för värdstack](./media/user-guide/usbx-events/image211.png)

**Beskrivning**
 
 Den här händelsen representerar en USBX-värdstack ny enhets create-händelse.

**Informationsfält**

- Informationsfält 1: Hcd.
- Informationsfält 2: Enhetsägare.
- Informationsfält 3: Portindex.
- Informationsfält 4: Enhet.

### <a name="host-stack-new-endpoint-create"></a>Skapa ny slutpunkt för värdstack 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Ikon** ![ Ikonen Skapa ny slutpunkt för värdstack](./media/user-guide/usbx-events/image212.png)

**Beskrivning**
 
Den här händelsen representerar en USBX-värdstack för att skapa en ny slutpunkt.

**Informationsfält**

- Informationsfält 1: Gränssnitt.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-root-hub-change-process"></a>Ändringsprocess för värdstackens rothubb 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Ikon** ![ Ikon för ändringsprocess för värdstackens rothubb](./media/user-guide/usbx-events/image213.png)

**Beskrivning**
 
Den här händelsen representerar en USBX-värdstacks rothubbändringsprocess.

**Informationsfält**

- Informationsfält 1: Portindex.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-root-hub-device-extraction"></a>Extrahering av rothubbenhet för värdstack 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Ikon** ![ Ikon för extrahering av rothubbenhet för värdstack](./media/user-guide/usbx-events/image214.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstack för extrahering av rothubbenhet.

**Informationsfält**

- Informationsfält 1: Hcd.
- Informationsfält 2: Portindex.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-root-hub-device-insertion"></a>Infogning av rothubbenhet för värdstack 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Ikon** ![ Ikon för infogning av rothubbenhet för värdstack](./media/user-guide/usbx-events/image215.png)

**Beskrivning**

Den här händelsen representerar en USBX-värdstack rothubbenhetsinmatning.

**Informationsfält**

- Informationsfält 1: Hcd.
- Informationsfält 2: Portindex.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="host-stack-transfer-request"></a>Överföringsbegäran för värdstack 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Ikon** ![ Ikonen Överföringsbegäran för värdstack](./media/user-guide/usbx-events/image216.png)

**Beskrivning**

Den här händelsen representerar en överföringsbegäran för EN USBX-värdstack.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Överföringsbegäran.
- Informationsfält 4: Används inte.

### <a name="host-stack-transfer-request-abort"></a>Begäran om att avbryta överföring av värdstack 

#### <a name="internal-io-driver-get-status"></a>Hämta status för intern I/O-drivrutin

**Ikon** ![ Ikonen Avbryt överföringsbegäran i värdstack](./media/user-guide/usbx-events/image217.png)

**Beskrivning**

Den här händelsen representerar ett avbrott i överföringsbegäran för USBX-värdstack.

**Informationsfält**

- Informationsfält 1: Enhet.
- Informationsfält 2: Slutpunkt.
- Informationsfält 3: Överföringsbegäran.
- Informationsfält 4: Används inte.

### <a name="usbx-error"></a>USBX-fel 

#### <a name="ux_error"></a>ux_error

**Ikon** ![ Ikon för U S B X-fel](./media/user-guide/usbx-events/image218.png)

**Beskrivning**

Den här händelsen representerar en USBX-felhändelse.

**Informationsfält**

- Informationsfält 1: USBX-fel.
- Informationsfält 2: Felnamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.