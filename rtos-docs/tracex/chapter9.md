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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="4fcf0-103">Kapitel 9 – Azure återställnings tider USBX trace Events</span><span class="sxs-lookup"><span data-stu-id="4fcf0-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="4fcf0-104">Det här kapitlet innehåller en beskrivning av de Azure återställnings tider USBX-händelser som visas av TraceX.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="4fcf0-105">Lista över händelser och ikoner</span><span class="sxs-lookup"><span data-stu-id="4fcf0-105">List of Events and Icons</span></span>

<span data-ttu-id="4fcf0-106">Följande är en lista över USBX-händelser som visas av TraceX.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="4fcf0-107">Ikon</span><span class="sxs-lookup"><span data-stu-id="4fcf0-107">Icon</span></span>                             | <span data-ttu-id="4fcf0-108">Innebörd</span><span class="sxs-lookup"><span data-stu-id="4fcf0-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![Enhets klass C D C Aktivera ikon](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="4fcf0-110">**Enhets klass CDC-aktivering** *(ux_device_class_cdc_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![Enhets klass C D C inaktivera ikon](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="4fcf0-112">**CDC-inaktive ring av enhets klass** *(ux_device_class_cdc_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![Enhets klass C D C Läs ikon](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="4fcf0-114">**Läsning av enhets klass CDC** *(ux_device_class_cdc_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![Enhets klass C D s Skriv ikon](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="4fcf0-116">**Enhets klass CDC-skrivning** *(ux_device_class_cdc_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![Dpump Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="4fcf0-118">**Aktivering av enhets klass Dpump** *(ux_device_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![Ikon för Dpump för enhets klass](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="4fcf0-120">**Dpump för enhets klass** *(ux_device_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![Läs ikon för enhets klassens Dpump](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="4fcf0-122">**Läsning av enhets klassens Dpump** *(ux_device_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![Dpump Skriv ikon för enhets klass](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="4fcf0-124">**Skrivning av enhets klass Dpump** *(ux_device_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![Ikon för HID-aktivering i enhets klass](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="4fcf0-126">**HID-aktivering för enhets klass** *(ux_device_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![Ikon för HID-inaktivera enhets klass](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="4fcf0-128">**HID-inaktive ring av enhets klass** *(ux_device_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![Ikon för att skicka HID-beskrivning för enhets klass](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="4fcf0-130">**Skicka HID-beskrivning för enhets klass** *(ux_device_class_hid_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![Ikonen Hämta ikon för enhets klassens HID-händelse](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="4fcf0-132">**Hämta HID-händelse för enhets klass** *(ux_device_class_hid_event_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![Ikon uppsättnings ikon för HID-händelseloggen i enhets klass](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="4fcf0-134">**HID-händelse uppsättning för enhets klass** *(ux_device_class_hid_event_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![Ikonen Hämta ikon för enhets klassens HID-rapport](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="4fcf0-136">**Hämta HID-rapport för enhets klass** *(ux_device_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![Ikon för HID-rapport för enhets klass](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="4fcf0-138">**HID-rapport uppsättning i enhets klass** *(ux_device_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![Pima Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="4fcf0-140">**Aktivering av enhets klass Pima** *(ux_device_class_pima_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![Ikon för Pima för enhets klass](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="4fcf0-142">**Pima för enhets klass** *(ux_device_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![Enhets klass Pima enhets information skicka ikon](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="4fcf0-144">**Skicka enhets information i enhets klass Pima** *(ux_device_class_pima_device_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![Enhets klass Pima händelse Hämta ikon](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="4fcf0-146">**Enhets klass Pima Event get** *(ux_device_class_pima_event_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![Enhets klass Pima händelse uppsättnings ikon](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="4fcf0-148">**Pima händelse uppsättning** *(Ux_device_class_pima_event_set)* för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![Enhets klass Pima objekt Lägg till ikon](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="4fcf0-150">**Enhets klass Pima objekt Lägg till** *(ux_device_class_pima_object_add)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![Enhets klass Pima objekt data hämta ikon](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="4fcf0-152">**Enhets klass Pima objekt data hämta** *(ux_device_class_pima_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![Ikon för att skicka Pima objekt data i enhets klass](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="4fcf0-154">**Skicka objekt data från enhets klass Pima** *(ux_device_class_pima_object_data_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![Pima objekt borttagnings ikon för enhets klass](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="4fcf0-156">**Enhets klass Pima objekt borttagning** *(ux_device_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![Skicka ikon för Pima objekt i enhets klass](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="4fcf0-158">**Pima objekt i enhets klass hanterar skicka** *(ux_device_class_pima_object_handles_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![Enhets klass Pima objekt information Hämta ikon](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="4fcf0-160">**Enhets klass Pima objekt information get** *(ux_device_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![Skicka ikon för Pima objekt information i enhets klass](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="4fcf0-162">**Skicka Pima objekt information** *(Ux_device_class_pima_object_info_send)* i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![Enhets klass Pima objekt nummer skicka ikon](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="4fcf0-164">Skicka *(ux_device_class_pima_objects_number_send)* **Pima objekt nummer i enhets klass**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![Enhets klass Pima del objekt data hämta ikon](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="4fcf0-166">**Enhets klass Pima del objekt data hämta** *(ux_device_class_pima_partial_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![Ikon för Pima svars sändning i enhets klass](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="4fcf0-168">**Pima för enhets klassens svar** *(ux_device_class_pima_response_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![Enhets klass Pima Storage I D-skicka ikon](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="4fcf0-170">**Enhets klass Pima lagrings-ID skicka** *(ux_device_class_pima_storage_id_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![Enhets klass Pima Storage information skicka ikon](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="4fcf0-172">**Sändning av Pima Storage-information i enhets klass** *(ux_device_class_pima_storage_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![Enhets klass R N D I S Aktivera ikon](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="4fcf0-174">**Aktivering av enhets klass RNDIS** *(ux_device_class_rndis_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![Ikonen enhets klass R N D I S inaktivera](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="4fcf0-176">**RNDIS för enhets klass** *(ux_device_class_rndis_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![Enhets klass R N D I S meddelande Behåll Aliveicon](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="4fcf0-178">**Enhets klass RNDIS meddelande Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![Ikon för enhets klass R N D N D I S](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="4fcf0-180">**RNDIS meddelande fråga för enhets klass** *(ux_device_class_rndis_msg_query)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![Enhets klass R N D I S ikon för meddelande återställning](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="4fcf0-182">**RNDIS meddelande återställning för enhets klass** *(ux_device_class_rndis_msg_reset)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![Ikon för enhets klass R N D N D I S](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="4fcf0-184">**RNDIS meddelande uppsättning för enhets klass** *(ux_device_class_rndis_msg_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![Enhets klass R N D N D I S paket mottagnings ikon](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="4fcf0-186">**Mottagning av enhets klassens RNDIS-paket** *(ux_device_class_rndis_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![Enhets klass R N D I S paket sändnings ikon](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="4fcf0-188">**RNDIS Packet överföring i enhets klass** *(ux_device_class_rndis_packet_transmit)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![Aktiverings ikon för enhets klass lagring](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="4fcf0-190">**Aktivering av enhets klass lagring** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![Ikon för enhets klassens lagrings inaktive rad](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="4fcf0-192">**Inaktive ring av enhets klass lagring** *(ux_device_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![Ikon för lagrings format för enhets klass](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="4fcf0-194">**Lagrings format för enhets klass** *(ux_device_class_storage_format)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![Ikon för enhets klass lagrings förfrågan](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="4fcf0-196">**Förfrågan om enhets klass lagring** *(ux_device_class_storage_inquiry)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![Enhets klassens lagrings läge Välj ikon](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="4fcf0-198">**Val av enhets klassens lagrings läge** *(ux_device_class_storage_mode_select)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![Ikon för lagrings läge i enhets klass](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="4fcf0-200">**Enhets klassens lagrings läge Sense** *(ux_device_class_storage_mode_sense)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![Enhets klass lagring förhindra att ikonen borttagning av media](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="4fcf0-202">**Enhets klass lagring förhindra borttagning av media** *(ux_device_class_storage_prevent_allow_media_removal)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![Läs ikon för enhets klass lagring](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="4fcf0-204">**Läsning av enhets klass lagring** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![Enhets klass lagring Läs kapacitets ikon](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="4fcf0-206">**Läs kapacitet för enhets klass lagring** *(ux_device_class_storage_read_capacity)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![Kapacitets ikon för Läs format för enhets klass lagring](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="4fcf0-208">**Kapacitet för läsning av enhets klass lagring** *(ux_device_class_storage_read_format_capacity)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![Enhets klass lagring läsa innehålls förtecknings ikon](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="4fcf0-210">**Läsa innehålls förteckning för enhets klass lagring** *(ux_device_class_storage_read_toc)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![Ikon för enhets klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="4fcf0-212">**Enhets klass Storage-begäran Sense** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![Start stopps ikon för enhets klass lagring](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="4fcf0-214">**Start stopp för enhets klass lagring** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![Ikon för lagrings test för enhets klass](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="4fcf0-216">**Test av enhets klass lagring är klar** *(ux_device_class_storage_test_ready)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![Enhets klass lagring verifiera ikon](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="4fcf0-218">**Verifiera lagring av enhets klass** *(ux_device_class_storage_verify)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![Skriv ikon för enhets klass lagring](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="4fcf0-220">**Lagrings skrivning av enhets klass** *(ux_device_class_storage_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![Alternativ inställnings ikon för enhets stack](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="4fcf0-222">**Alternativ inställning för enhets stack Hämta** *(ux_device_stack_alternate_setting_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![Ikon för alternativ inställnings uppsättning för enhets stack](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="4fcf0-224">**Alternativ inställnings uppsättning för enhets stack** *(ux_device_stack_alternate_setting_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![Enhets Stack klass register ikon](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="4fcf0-226">**Enhets Stack klass register** *(ux_device_stack_class_register)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![Enhets stack rensa funktions ikon](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="4fcf0-228">**Rensnings funktion för enhets stack** *(ux_device_stack_clear_feature)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![Hämta ikon för enhets stack konfiguration](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="4fcf0-230">**Hämta enhets stack konfiguration** *(ux_device_stack_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![Ikon för enhets stack konfigurations uppsättning](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="4fcf0-232">**Konfigurations uppsättning för enhets stack** *(ux_device_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![Enhets stackens anslutnings ikon](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="4fcf0-234">**Enhets stack anslutning** *(ux_device_stack_connect)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![Ikon för att skicka enhets stack Beskrivning](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="4fcf0-236">**Skicka enhets Stacks Beskrivning** *(ux_device_stack_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![Ikon för enhets stack från koppling](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="4fcf0-238">**Enhets stack från koppling** *(ux_device_stack_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![Ikon för enhets stackens slut punkts bås](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="4fcf0-240">**Enhets stackens slut punkts ficka** *(ux_device_stack_endpoint_stall)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![Enhets stack Hämta status ikon](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="4fcf0-242">**Enhets stack Hämta status** *(ux_device_stack_get_status)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![Aktiverings ikon för värd för enhets stack](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="4fcf0-244">**Aktivering av enhets stack värd** *(ux_device_stack_host_wakeup)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![Ikon för enhets stack initierare](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="4fcf0-246">**Initiera enhets stack** *(ux_device_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![Borttagnings ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="4fcf0-248">**Borttagning av enhets Stacks gränssnitt** *(ux_device_stack_interface_delete)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![Hämta ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="4fcf0-250">**Hämta enhets stack gränssnitt** *(ux_device_stack_interface_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![Ikon för enhets stackens gränssnitts uppsättning](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="4fcf0-252">**Enhets stack gränssnitts uppsättning** *(ux_device_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![Funktions ikon för enhets stack uppsättning](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="4fcf0-254">**Enhets stack uppsättnings funktion** *(ux_device_stack_set_feature)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![Avbrotts ikon för enhets stack överföring](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="4fcf0-256">**Avbrotts överföring av enhets stack** *(ux_device_stack_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\* Ikon för enhets stacken överför alla begär Anden Avbryt](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="4fcf0-258">**Enhets stack överför alla begäran om att avbryta begäran** *(ux_device_stack_transfer_all_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![Ikon för begäran om enhets stack-överföring](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="4fcf0-260">**Begäran om enhets stack överföring** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![Asix Aktivera ikon för värd klass](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="4fcf0-262">**Aktivering av värd klass Asix** *(ux_host_class_asix_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![Asix-ikon för värd klass](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="4fcf0-264">**Asix inaktive ring av värd klass** *(ux_host_class_asix_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![Asix för värd klassens avbrotts meddelande](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="4fcf0-266">**Avbrotts meddelande för värd klass Asix** *(ux_host_class_asix_interrupt_notification)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![Läs ikon för värd klassen Asix](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="4fcf0-268">**Läsning av värd klass Asix** *(ux_host_class_asix_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![Asix Skriv ikon för värd klass](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="4fcf0-270">**Skrivning av värd klass Asix** *(ux_host_class_asix_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![Ikon för ljud aktivering i värd klass](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="4fcf0-272">**Ljud aktivering av värd klass** *(ux_host_class_audio_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![Ikonen Hämta ljud kontroll värde i värd klass](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="4fcf0-274">**Hämta ljud kontroll värde i värd klass** *(ux_host_class_audio_control_value_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![Ikon för ljud kontroll värde för värd klass](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="4fcf0-276">**Ljud kontroll värdes uppsättning i värd klass** *(ux_host_class_audio_control_value_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![Ikon för ljud inaktive ring av värd klass](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="4fcf0-278">**Ljud inaktive ring av värd klass** *(ux_host_class_audio_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![Ljud läsnings ikon för värd klass](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="4fcf0-280">**Ljud läsning av värd klass** *(ux_host_class_audio_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![Exempel på hämtnings ikon för värd klassens ljud strömning](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="4fcf0-282">**Exempel på ljud uppspelning av värd klass för hämtning** *(ux_host_class_audio_streaming_sampling_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![Ikon för samplings uppsättning för värd klassens ljud strömning](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="4fcf0-284">**Provtagnings uppsättning för ljud strömning i värd klass** *(ux_host_class_audio_streaming_sampling_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![Ljud Skriv ikon för värd klass](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="4fcf0-286">**Ljud skrivning av värd klass** *(ux_host_class_audio_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![Värd klass C D C A C M Aktivera ikon](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="4fcf0-288">**Värd klass CDC ACM Activate** *(ux_host_class_cdc_acm_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![Värd klass C D C A C M inaktivera ikon](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="4fcf0-290">**Värd klass CDC ACM-inaktive rad** *(ux_host_class_cdc_acm_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![Värd klass C D A C M I O C T L i pipe-ikon](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="4fcf0-292">**Värd klass CDC ACM IOCTL abort i pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![Värd klass C D C A C M I O C T L ta bort pipe-ikon](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="4fcf0-294">**Värd klass CDC ACM IOCTL avbryter pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![Värd klass C D C A C M I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="4fcf0-296">**Värd klass CDC ACM IOCTL get enhets status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![Värd klass C D C A C M I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="4fcf0-298">**Värd klass CDC ACM IOCTL get line** *-kodning (ux_host_class_cdc_acm_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![Värd klass C D C A C M I O C T L ikon för återanrop i meddelande](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="4fcf0-300">**Värd klass CDC ACM IOCTL Notification motringning** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![Värd klass C D C A C M I O C T L-ikonen skicka rast](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="4fcf0-302">**Värd klass CDC ACM IOCTL Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![Värd klass C D C A C M I O C T L ange rad kodnings ikon](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="4fcf0-304">**Värd klass CDC ACM IOCTL set line** *-kodning (ux_host_class_cdc_acm_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![Värd klass C D C A C M I O C T L ikon för ange linje tillstånd](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="4fcf0-306">**Värd klass CDC ACM IOCTL set line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![Värd klass C D A C M Läs ikon](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="4fcf0-308">**Värd klass CDC ACM Read** *(ux_host_class_cdc_acm_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![Start ikon för värd klass C D A C M](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="4fcf0-310">**Start av värd klass CDC-ACM** *(ux_host_class_cdc_acm_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![Svars ikon för värd klass C D A C M](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="4fcf0-312">**ACM för värd klass CDC-mottagning** *(ux_host_class_cdc_acm_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![Värd klass C D A C M Skriv ikon](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="4fcf0-314">**Värd klass CDC ACM Write** *(ux_host_class_cdc_acm_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![Dpump Aktivera ikon för värd klass](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="4fcf0-316">**Aktivering av värd klass Dpump** *(ux_host_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![Dpump-ikon för värd klass](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="4fcf0-318">**Dpump inaktive ring av värd klass** *(ux_host_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![Läs ikon för värd klassen Dpump](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="4fcf0-320">**Läsning av värd klass Dpump** *(ux_host_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![Dpump Skriv ikon för värd klass](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="4fcf0-322">**Skrivning av värd klass Dpump** *(ux_host_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![Ikon för HID-aktivering i värd klass](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="4fcf0-324">**HID-aktivering för värd klass** *(ux_host_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![Register ikon för HID-klient för värd klass](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="4fcf0-326">**HID-klient register för värd klass** *(ux_host_class_hid_client_register)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![Ikon för HID-inaktivera värd klass](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="4fcf0-328">**HID-inaktive ring av värd klass** *(ux_host_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![Ikon för HID-inaktivitet i värd klass](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="4fcf0-330">**HID Idle-inaktivitet i värd klass** *(ux_host_class_hid_idle_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![Ikon för HID inaktive rad värd klass](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="4fcf0-332">**HID Idle-uppsättning** *(Ux_host_class_hid_idle_set)* för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![Ikon för HID-tangentbordet för värd klass](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="4fcf0-334">**Aktivera HID-tangentbordet för värd klass** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![Ikonen värd klass HID tangent bords inaktive ring](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="4fcf0-336">**HID-tangentbordsmus för värd klass** *(ux_host_class_hid_keyboard_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![Aktivera ikon för HID-mus i värd klass](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="4fcf0-338">**Aktivera HID-mus för värd klass** *(ux_host_class_hid_mouse_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![Värd klass HID-mus inaktivera ikon](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="4fcf0-340">**Värd klass HID-mus inaktive rad** *(ux_host_class_hid_mouse_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![Ikonen aktivera HID-fjärrstyrning i värd klass](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="4fcf0-342">**Aktivera HID-fjärrstyrning av värd klass** *(ux_host_class_hid_remote_control_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![Ikon för HID-fjärrstyrning av värd klass](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="4fcf0-344">**HID-fjärrstyrning av värd klass** *(ux_host_class_hid_remote_control_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![Ikon för Hämta värd klass HID-rapport](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="4fcf0-346">**Hämta HID-rapport för värd klass** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![Ikon för HID-rapport för värd klass](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="4fcf0-348">**HID-rapport uppsättning för värd klass** *(ux_host_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![Aktivera ikon för värd klassens hubb](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="4fcf0-350">**Aktivera värd klass hubb** *(ux_host_class_hub_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![Identifiera ikon för värd klassens hubb ändring](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="4fcf0-352">**Identifiera ändring av värd klassens hubb** *(ux_host_class_hub_change_detect)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\* Ikon för att inaktivera värd Klasss hubb](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="4fcf0-354">**Inaktive ring av värd klassens hubb** *(ux_host_class_hub_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![Ikon för att ändra anslutnings process för värd klassens hubb port](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="4fcf0-356">**Anslutnings process för port ändring i värd klass** *(ux_host_class_hub_port_change_connection_process)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![Aktivera process ikon för värd klassens hubb port ändring](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="4fcf0-358">**Aktiverings process för port ändring i värd klass** *(ux_host_class_hub_port_change_enable_process)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![Port ändring över ikon för värd Klasss hubb över den aktuella process ikonen](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="4fcf0-360">**Port ändring i värd klassens hubb över den aktuella processen** *(ux_host_class_hub_port_change_over_current_process)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![Ikon för ändrings process för värd klassens Hubbs port](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="4fcf0-362">**Återställnings process för port ändring av värd klass** *(ux_host_class_hub_port_change_reset_process)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![Ikon för att inaktivera process klassens hubb port ändring](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="4fcf0-364">Inaktive ring av **värd klassens nav port ändrings process** *(ux_host_class_hub_port_change_suspend_process)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![Pima Aktivera ikon för värd klass](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="4fcf0-366">**Aktivering av värd klass Pima** *(ux_host_class_prima_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![Pima-ikon för värd klass](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="4fcf0-368">**Pima inaktive ring av värd klass** *(ux_host_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![Hämta ikon för värd klassens Pima enhets information](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="4fcf0-370">**Hämta Pima enhets information för värd klass** *(ux_host_class_pima_device_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![Enhets återställnings ikon för värd klass Pima](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="4fcf0-372">**Enhets återställning för Pima av värd klass** *(ux_host_class_pima_device_reset)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![Meddelande ikon för värd klass Pima](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="4fcf0-374">**Pima-meddelande för värd klass** *(ux_host_class_pima_notification)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![Ikon för Pima för värd klassens antal objekt](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="4fcf0-376">**Pima antal objekt för värd klass hämtning** *(ux_host_class_pima_num_objects_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![Ikonen Stäng Pima objekt i värd klass](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="4fcf0-378">**Pima objekt stängning för värd klass** *(ux_host_class_pima_object_close)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![Objekt kopierings ikon för värd klass Pima](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="4fcf0-380">**Objekts kopia av värd klassens Pima** *(ux_host_class_pima_object_copy)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![Pima objekt borttagnings ikon för värd klass](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="4fcf0-382">**Ta bort värd klass Pima objekt** *(ux_host_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![Pima objekt Hämta ikon för värd klass](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="4fcf0-384">**Hämta värd klass Pima objekt** *(ux_host_class_pima_object_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![Hämta ikon för värd klassens Pima objekt information](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="4fcf0-386">**Hämta Pima för värd klassens objekt information** *(ux_host_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![Skicka ikon för Pima objekt information i värd klass](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="4fcf0-388">**Sändning av Pima objekt information i värd klass** *(ux_host_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![Ikon för flytt av Pima objekt i värd klass](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="4fcf0-390">**Flytt av Pima objekt i värd klass** *(ux_host_class_pima_object_move)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![Ikon för att skicka Pima objekt i värd klass](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="4fcf0-392">**Skicka Pima objekt i värd klass** *(ux_host_class_pima_object_send)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![Avbrotts ikon för Pima objekt överföring i värd klass](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="4fcf0-394">**Avbryt Pima objekt överföring i värd klass** *(ux_host_class_object_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![Läs ikon för värd klassen Pima](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="4fcf0-396">**Läsning av värd klass Pima** *(ux_host_class_pima_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![Ikon för Pima-begäran i värd klass](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="4fcf0-398">**Pima-begäran för värd klass Avbryt** *(ux_host_class_pima_request_cancel)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![Pima för värd klassens stängnings ikon](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="4fcf0-400">**Pima-session för värd klass stängs** *(ux_host_class_pima_session_close)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![Öppna Pima-ikonen för värd klassens session](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="4fcf0-402">**Pima-session för värd klass öppen** *(ux_host_class_pima_session_open)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![Pima lagrings-ID Hämta ikon för värd klass](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="4fcf0-404">**Pima lagrings-ID: n** *(Ux_host_class_pima_storage_ids_get)* för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![Pima Storage information get-ikon i värd klass](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="4fcf0-406">**Pima Storage information get** *(Ux_host_class_pima_storage_info_get)* i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![Ikon för Pima för värd klass](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="4fcf0-408">**Pima-skjutreglage för värd klass** *(ux_host_class_pima_thumb_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![Pima Skriv ikon för värd klass](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="4fcf0-410">**Skrivning av värd klass Pima** *(ux_host_class_pima_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![Aktivera ikon för värd klass skrivare](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="4fcf0-412">**Aktivera värd klass skrivare** *(ux_host_class_printer_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![Ikon för att inaktivera värd klass skrivare](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="4fcf0-414">**Inaktive ring av värd klass skrivare** *(ux_host_class_printer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![Hämta ikon för värd klassens skrivar namn](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="4fcf0-416">**Skrivar namn för värd klass Hämta** *(ux_host_class_printer_name_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![Läs ikon för värd klass skrivare](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="4fcf0-418">**Läsning av värd klass skrivare** *(ux_host_class_printer_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![Ikon för mjuk återställning av värd klass skrivare](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="4fcf0-420">**Mjuk återställning av värd klass skrivare** *(ux_host_class_printer_soft_reset)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![Ikon för Hämta värd klass skrivar status](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="4fcf0-422">**Hämta status för värd klass skrivare** *(ux_host_class_printer_status_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![Skriv ikon för värd klass skrivare](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="4fcf0-424">**Skrivning av värd klass skrivare** *(ux_host_class_printer_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![Prolific Aktivera ikon för värd klass](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="4fcf0-426">**Aktivering av värd klass Prolific** *(ux_host_class_prolific_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![Prolific-ikon för värd klass](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="4fcf0-428">**Prolific inaktive ring av värd klass** *(ux_host_class_prolific_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![Prolific för värd klass I O C T L Avbryt i pipe-ikon](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="4fcf0-430">**Värd klass Prolific IOCTL Avbryt i pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![Prolific för värd klass I O C T L ta bort pipe-ikon](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="4fcf0-432">**Prolific för värd klass IOCTL avbryter pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![Prolific för värd klass I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="4fcf0-434">**Värd klass Prolific IOCTL get enhets status** *(ux_host_class_prolific_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![Prolific för värd klass I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="4fcf0-436">**Prolific för värd klass IOCTL get line-kodning** *(ux_host_class_prolific_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![Prolific för värd klass I O C T L ta bort ikon](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="4fcf0-438">**Prolific IOCTL-rensning i värd klass** *(ux_host_class_prolific_ioctl_purge)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![Enhets status ändrings ikon för värd klass Prolific I O d T L](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="4fcf0-440">**Status ändring för Prolific IOCTL-rapport enhets status i värd klass** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![Prolific för värd klass I O C T L](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="4fcf0-442">**Sändning av värd klass Prolific IOCTL skicka rast** *(ux_host_class_prolific_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![Prolific för värd klass I O C T L ange rad kodnings ikon](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="4fcf0-444">**Prolific för värd klassens IOCTL-uppsättning** *(ux_host_class_prolific_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![Ikon för värd klass Prolific I O C T L](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="4fcf0-446">**Prolific IOCTL ange linje tillstånd** *(Ux_host_class_prolific_ioctl_set_line_state)* i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![Läs ikon för värd klassen Prolific](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="4fcf0-448">**Läsning av värd klass Prolific** *(ux_host_class_prolific_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![Start ikon för Prolific mottagning i värd klass](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="4fcf0-450">**Start av värd klass Prolific mottagning** *(ux_host_class_prolific_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![Stopp ikon för Prolific för värd klass](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="4fcf0-452">**Prolific för värd klassens mottagnings stopp** *(ux_host_class_prolific_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![Prolific Skriv ikon för värd klass](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="4fcf0-454">**Skrivning av värd klass Prolific** *(ux_host_class_prolific_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![Aktivera ikon för värd klass lagring](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="4fcf0-456">**Aktivering av värd klass lagring** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![Ikon för värd klass lagrings inaktive ring](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="4fcf0-458">**Inaktive ring av värd klass lagring** (*ux_host_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![Ikon för Hämta värd klass lagrings medie kapacitet](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="4fcf0-460">**Hämtning av värd klass lagrings medie kapacitet** *(ux_host_class_storage_media_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![Ikon för Hämta kapacitet för värd klass lagrings medie format](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="4fcf0-462">**Hämtnings kapacitet för värd klass lagrings medie format** *(ux_host_class_storage_media_format_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![Monterings ikon för värd klass lagrings medium](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="4fcf0-464">**Värd klass lagrings medie montering** (ux_host_class_storage_media_mount) \*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![Öppnings ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="4fcf0-466">**Värd klass lagrings medium öppet** *(ux_host_class_storage_media_open)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![Läs ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="4fcf0-468">**Läsning av värd klassens lagrings medium** *(ux_host_class_storage_media_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![Skriv ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="4fcf0-470">**Skrivning av värd klass lagrings medium** *(ux_host_class_storage_media_write)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![Ikon för värd klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="4fcf0-472">**Sense-begäran för värd klass lagring** *(ux_host_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![Start stopp ikon för värd klass lagring](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="4fcf0-474">**Start stopp för värd klass lagring** *(ux_host_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![Test ikon för värd klassens lagrings enhet](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="4fcf0-476">**Redo test för värd klass lagrings enhet** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![Ikon för att skapa värd Stack klass instans](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="4fcf0-478">**Värd Stack klass instans skapa** *(ux_host_stack_class_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![Ikon för att förstöra värd Stack klass instans](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="4fcf0-480">**Förstöring av värd Stack klass instans** *(ux_host_stack_class_instance_destroy)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![Borttagnings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="4fcf0-482">**Ta bort värd stack konfiguration** *(ux_host_stack_configuration_delete)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![Uppräknings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="4fcf0-484">**Uppräkning av värd stack konfiguration** *(ux_host_stack_configuration_enumerate)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![Ikon för att skapa värd stack konfigurations instans](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="4fcf0-486">**Skapa värd stack konfigurations instans** *(ux_host_stack_configuration_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![Borttagnings ikon för värd Stacks konfigurations instans](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="4fcf0-488">**Borttagning av värd Stacks konfigurations instans** *(ux_host_stack_configuration_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![Ikon för konfigurations uppsättning för värd stack](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="4fcf0-490">**Konfigurations uppsättning för värd stack** *(ux_host_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![Ikon för värd stack enhetens adress uppsättning](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="4fcf0-492">**Adress uppsättning för värd stack enhet** *(ux_host_stack_device_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![Hämta ikon för värd stack enhets konfiguration](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="4fcf0-494">**Hämtning av värd stack enhets konfiguration** *(ux_host_stack_device_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![Konfiguration av värd stack enhets konfiguration Välj ikon](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="4fcf0-496">**Konfiguration av värd stack enhets konfiguration Välj** *(ux_host_stack_device_configuration_select)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![Läs ikon för värd stack enhets Beskrivning](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="4fcf0-498">**Läsning av värd stack enhets Beskrivning** *(ux_host_stack_device_descriptor_read)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![Hämta ikon för värd stack enhet](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="4fcf0-500">**Värd stack enhet Hämta** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![Ikon för att ta bort värd stack enhet](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="4fcf0-502">**Ta bort värd stack enhet** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![Ikon för värd stack för enhets resurs](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="4fcf0-504">**Värd stack enhets resurs kostnads fritt** (ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![Ikon för att skapa värd stack slut punkts instans](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="4fcf0-506">**Skapa värd stack slut punkts instans** (ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![Borttagnings ikon för värd stack slut punkts instans](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="4fcf0-508">**Borttagning av värd stack slut punkts instans** (ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![Ikon för återställning av värd stack slut punkt](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="4fcf0-510">**Återställning av värd stack slut punkt** (ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![Avbryt ikon för värd stack slut punkts överföring](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="4fcf0-512">**Avbryt överföring av värd stack slut punkt** (ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![Registrerings ikon för värd stack värd styrenhet](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="4fcf0-514">Värd **styrenhets register värd styrenhet** *(ux_host_stack_hcd_register)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![Ikon för att initiera värd stack](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="4fcf0-516">**Värd stack initiering** *(ux_host_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![Hämta ikon för värd stackens gränssnitts slut punkt](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="4fcf0-518">**Hämtnings punkt för värd stack gränssnitt** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![Ikon för att skapa värd stack gränssnitts instans](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="4fcf0-520">**Värd stack gränssnitts instans skapa** *(ux_host_stack_interface_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![Borttagnings ikon för värd stackens gränssnitts instans](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="4fcf0-522">**Borttagning av värd Stacks gränssnitts instans** *(ux_host_stack_interface_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![Ikon för värd stack gränssnitts uppsättning](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="4fcf0-524">**Värd stack gränssnitts uppsättning** *(ux_host_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![Inställnings ikon för värd Stacks gränssnitt](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="4fcf0-526">**Välj värd stack gränssnitts inställning** *(ux_host_stack_interface_setting_select)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![Värd stack ny ikon för att skapa konfiguration](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="4fcf0-528">**Värd stack ny konfiguration skapa** *(ux_host_stack_new_configuration_create)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![Ikon för att skapa en ny enhet för värd stack](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="4fcf0-530">**Värd stack ny enhet skapa** *(ux_host_stack_new_device_create)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![Skapa ikon för värd stack för ny slut punkt](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="4fcf0-532">**Skapa en ny slut punkt för värd stacken** *(ux_host_stack_new_endpoint_create)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![Ikon för ändrings process för värd stackens rot nav](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="4fcf0-534">**Ändrings process för stacken i värd stacken** *(ux_host_stack_rh_change_process)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![Ikon för extrahering av värd stack för rot nav](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="4fcf0-536">**Värd stack för rot nav för enhet** *(ux_host_stack_rh_device_extraction)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![Ikon för värd stack för rot nav enhet](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="4fcf0-538">**Värd stack rot nav för enhets infogning** *(ux_host_stack_rh_device_insertion)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![Ikon för värd stack överförings förfrågan](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="4fcf0-540">**Begäran om värd-stack-överföring** *(ux_host_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![Avbryt ikon för begäran om värd stack överföring](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="4fcf0-542">**Avbrott i värd stack överförings förfrågan** *(ux_host_stack_transfer_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![Fel ikon för U S B X](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="4fcf0-544">**USBX-fel** *(ux_error)*</span><span class="sxs-lookup"><span data-stu-id="4fcf0-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="4fcf0-545">Händelse beskrivningar</span><span class="sxs-lookup"><span data-stu-id="4fcf0-545">Event Descriptions</span></span>

<span data-ttu-id="4fcf0-546">Följande sidor beskriver USBX spårnings händelser.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="4fcf0-547">Enhets klass CDC-aktivering</span><span class="sxs-lookup"><span data-stu-id="4fcf0-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="4fcf0-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="4fcf0-549">**Ikonen** ![ Enhets klass C D C Aktivera ikon](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="4fcf0-550">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-550">**Description**</span></span>

<span data-ttu-id="4fcf0-551">Den här händelsen representerar en USBX enhets klass CDC-aktiverings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="4fcf0-552">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-552">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-553">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-554">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-555">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-556">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="4fcf0-557">CDC-inaktive ring av enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="4fcf0-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="4fcf0-559">**Ikonen** ![ Enhets klass C D C inaktivera ikon](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="4fcf0-560">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-560">**Description**</span></span>

<span data-ttu-id="4fcf0-561">Den här händelsen representerar en USBX enhets klass CDC-inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="4fcf0-562">Informations fält</span><span class="sxs-lookup"><span data-stu-id="4fcf0-562">Information Fields</span></span> 

- <span data-ttu-id="4fcf0-563">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-564">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-565">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-566">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="4fcf0-567">Läsning av enhets klass CDC</span><span class="sxs-lookup"><span data-stu-id="4fcf0-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="4fcf0-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="4fcf0-569">**Ikonen** ![ Enhets klass C D C Läs ikon](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="4fcf0-570">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-570">**Description**</span></span>

<span data-ttu-id="4fcf0-571">Den här händelsen representerar läsnings händelsen för en USBX-enhets klass CDC.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="4fcf0-572">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-572">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-573">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-574">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-575">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-576">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="4fcf0-577">Enhets klass CDC-skrivning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="4fcf0-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="4fcf0-579">**Ikonen** ![ Enhets klass C D s Skriv ikon](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="4fcf0-580">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-580">**Description**</span></span>

<span data-ttu-id="4fcf0-581">Den här händelsen representerar en skrivnings händelse för USBX-enhetens klass CDC.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="4fcf0-582">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-582">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-583">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-584">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-585">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-586">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="4fcf0-587">Aktivering av enhets klass Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="4fcf0-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="4fcf0-589">**Ikonen** ![ Dpump Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="4fcf0-590">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-590">**Description**</span></span>

<span data-ttu-id="4fcf0-591">Den här händelsen representerar en USBX enhets klass Dpump aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="4fcf0-592">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-592">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-593">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-594">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-595">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-596">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="4fcf0-597">Inaktive ring av enhets klass Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="4fcf0-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="4fcf0-599">**Ikonen** ![ Ikon för Dpump för enhets klass](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="4fcf0-600">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-600">**Description**</span></span>

<span data-ttu-id="4fcf0-601">Den här händelsen representerar en USBX enhets klass Dpump-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-602">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-602">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-603">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-604">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-605">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-606">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="4fcf0-607">Läsning av enhets klassens Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="4fcf0-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="4fcf0-609">**Ikonen** ![ Läs ikon för enhets klassens Dpump](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="4fcf0-610">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-610">**Description**</span></span>

<span data-ttu-id="4fcf0-611">Den här händelsen representerar en USBX enhets klass Dpump Read event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="4fcf0-612">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-612">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-613">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-614">Info fält 2: buffert.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="4fcf0-615">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-616">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="4fcf0-617">Skrivning av enhets klass Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="4fcf0-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="4fcf0-619">**Ikonen** ![ Dpump Skriv ikon för enhets klass](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="4fcf0-620">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-620">**Description**</span></span>

<span data-ttu-id="4fcf0-621">Den här händelsen representerar en USBX enhets klass Dpump Skriv händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="4fcf0-622">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-622">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-623">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-624">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-625">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-626">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="4fcf0-627">HID-aktivering för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="4fcf0-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="4fcf0-629">**Ikonen** ![ Ikon för HID-aktivering i enhets klass](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="4fcf0-630">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-630">**Description**</span></span>

<span data-ttu-id="4fcf0-631">Den här händelsen representerar en USBX enhets klass HID Activate-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="4fcf0-632">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-632">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-633">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-634">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-635">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-636">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="4fcf0-637">HID-inaktive ring av enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="4fcf0-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="4fcf0-639">**Ikonen** ![ Ikon för HID-inaktivera enhets klass](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="4fcf0-640">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-640">**Description**</span></span>

<span data-ttu-id="4fcf0-641">Den här händelsen representerar en händelse för HID-inaktive ring av USBX enhets klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-642">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-642">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-643">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-644">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-645">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-646">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="4fcf0-647">Skicka HID-beskrivning för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="4fcf0-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="4fcf0-649">**Ikonen** ![ Ikon för att skicka HID-beskrivning för enhets klass](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="4fcf0-650">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-650">**Description**</span></span>

<span data-ttu-id="4fcf0-651">Den här händelsen representerar en USBX enhets klass som en händelse för att skicka HID-beskrivning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="4fcf0-652">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-652">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-653">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-654">Informations fält 2: beskrivnings typ.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4fcf0-655">Informations fält 3: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4fcf0-656">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="4fcf0-657">Hämta HID-händelse för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="4fcf0-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="4fcf0-659">**Ikonen** ![ Ikonen Hämta ikon för enhets klassens HID-händelse](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="4fcf0-660">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-660">**Description**</span></span>

<span data-ttu-id="4fcf0-661">Den här händelsen representerar en USBX enhets klass HID Event get event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="4fcf0-662">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-662">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-663">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-664">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-665">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-666">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="4fcf0-667">HID-händelse uppsättning för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="4fcf0-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="4fcf0-669">**Ikonen** ![ Ikon uppsättnings ikon för HID-händelseloggen i enhets klass](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="4fcf0-670">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-670">**Description**</span></span>

<span data-ttu-id="4fcf0-671">Den här händelsen representerar en HID-USBX för enhets klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="4fcf0-672">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-672">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-673">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-674">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-675">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-676">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="4fcf0-677">Hämta HID-rapport för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="4fcf0-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="4fcf0-679">**Ikonen** ![ Ikonen Hämta ikon för enhets klassens HID-rapport](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="4fcf0-680">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-680">**Description**</span></span>

<span data-ttu-id="4fcf0-681">Den här händelsen representerar en USBX enhets klass HID Report get event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="4fcf0-682">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-682">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-683">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-684">Informations fält 2: beskrivnings typ.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4fcf0-685">Informations fält 3: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4fcf0-686">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="4fcf0-687">HID-rapport uppsättning för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="4fcf0-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="4fcf0-689">**Ikonen** ![ Ikon för HID-rapport för enhets klass](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="4fcf0-690">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-690">**Description**</span></span>

<span data-ttu-id="4fcf0-691">Den här händelsen representerar en händelse för en HID-rapport för USBX-enhets klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="4fcf0-692">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-692">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-693">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-694">Informations fält 2: beskrivnings typ.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4fcf0-695">Informations fält 3: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4fcf0-696">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="4fcf0-697">Aktivering av enhets klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="4fcf0-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="4fcf0-699">**Ikonen** ![ Pima Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="4fcf0-700">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-700">**Description**</span></span>

<span data-ttu-id="4fcf0-701">Den här händelsen representerar en USBX enhets klass Pima aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="4fcf0-702">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-702">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-703">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-704">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-705">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-706">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="4fcf0-707">Inaktive ring av enhets klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="4fcf0-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="4fcf0-709">**Ikonen** ![ Ikon för Pima för enhets klass](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="4fcf0-710">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-710">**Description**</span></span>

<span data-ttu-id="4fcf0-711">Den här händelsen representerar en USBX enhets klass Pima-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-712">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-712">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-713">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-714">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-715">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-716">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="4fcf0-717">Skicka enhets information i enhets klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="4fcf0-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="4fcf0-719">**Ikonen** ![ Enhets klass Pima enhets information skicka ikon](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="4fcf0-720">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-720">**Description**</span></span>

<span data-ttu-id="4fcf0-721">Den här händelsen representerar en USBX enhets klass Pima skicka händelse för enhets information.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="4fcf0-722">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-722">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-723">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-724">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-725">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="4fcf0-726">Hämta Pima-händelse i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="4fcf0-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="4fcf0-728">**Ikonen** ![ Enhets klass Pima händelse Hämta ikon](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="4fcf0-729">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-729">**Description**</span></span>

<span data-ttu-id="4fcf0-730">Den här händelsen representerar en USBX enhets klass Pima Event get event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="4fcf0-731">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-731">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-732">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-733">Info fält 2: Pima-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="4fcf0-734">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-735">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="4fcf0-736">Pima händelse uppsättning för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="4fcf0-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="4fcf0-738">**Ikonen** ![ Enhets klass Pima händelse uppsättnings ikon](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="4fcf0-739">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-739">**Description**</span></span>

<span data-ttu-id="4fcf0-740">Den här händelsen representerar händelse uppsättnings händelsen för en USBX enhets klass Pima.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="4fcf0-741">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-741">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-742">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-743">Info fält 2: Pima-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="4fcf0-744">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-745">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="4fcf0-746">Enhets klass Pima objekt Lägg till</span><span class="sxs-lookup"><span data-stu-id="4fcf0-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="4fcf0-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="4fcf0-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="4fcf0-748">**Ikonen** ![ Enhets klass Pima objekt Lägg till ikon](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="4fcf0-749">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-749">**Description**</span></span>

<span data-ttu-id="4fcf0-750">Den här händelsen representerar en USBX enhets klass Pima objekt Lägg till händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="4fcf0-751">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-751">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-752">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-753">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-754">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-755">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="4fcf0-756">Hämta Pima objekt data för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="4fcf0-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="4fcf0-758">**Ikonen** ![ Enhets klass Pima objekt data hämta ikon](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="4fcf0-759">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-759">**Description**</span></span>

<span data-ttu-id="4fcf0-760">Den här händelsen representerar en USBX enhets klass Pima objekt data hämta händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="4fcf0-761">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-761">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-762">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-763">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-764">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-765">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="4fcf0-766">Skicka objekt data från enhets klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="4fcf0-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="4fcf0-768">**Ikonen** ![ Ikon för att skicka Pima objekt data i enhets klass](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="4fcf0-769">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-769">**Description**</span></span>

<span data-ttu-id="4fcf0-770">Den här händelsen representerar en USBX enhets klass Pima objekt data sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="4fcf0-771">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-771">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-772">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-773">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-774">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-775">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="4fcf0-776">Ta bort Pima objekt i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="4fcf0-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="4fcf0-778">**Ikonen** ![ Pima objekt borttagnings ikon för enhets klass](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="4fcf0-779">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-779">**Description**</span></span>

<span data-ttu-id="4fcf0-780">Den här händelsen representerar en USBX enhets klass Pima objekt Delete event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="4fcf0-781">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-781">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-782">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-783">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-784">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-785">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="4fcf0-786">Skicka i enhets klassens Pima-objekt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="4fcf0-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="4fcf0-788">**Ikonen** ![ Skicka ikon för Pima objekt i enhets klass](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="4fcf0-789">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-789">**Description**</span></span>

<span data-ttu-id="4fcf0-790">Den här händelsen representerar en USBX enhets klass Pima objekt som skickar händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="4fcf0-791">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-791">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-792">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-793">Informations fält 2: lagrings-ID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4fcf0-794">Info-fält 3: kod för objekt format.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="4fcf0-795">Info-fält 4: objekt Association.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="4fcf0-796">Hämta Pima objekt information för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4fcf0-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4fcf0-798">**Ikonen** ![ Enhets klass Pima objekt information Hämta ikon](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="4fcf0-799">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-799">**Description**</span></span>

<span data-ttu-id="4fcf0-800">Den här händelsen representerar en USBX enhets klass Pima objekt information get-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="4fcf0-801">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-801">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-802">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-803">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-804">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-805">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="4fcf0-806">Skicka Pima objekt information i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4fcf0-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4fcf0-808">**Ikonen** ![ Skicka ikon för Pima objekt information i enhets klass](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="4fcf0-809">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-809">**Description**</span></span>

<span data-ttu-id="4fcf0-810">Den här händelsen representerar en USBX enhets klass Pima objekt information skicka händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="4fcf0-811">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-811">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-812">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-813">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-814">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-815">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="4fcf0-816">Skicka Pima objekt nummer i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="4fcf0-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="4fcf0-818">**Ikonen** ![ Enhets klass Pima objekt nummer skicka ikon](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="4fcf0-819">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-819">**Description**</span></span>

<span data-ttu-id="4fcf0-820">Den här händelsen representerar en USBX enhets klass Pima objekt nummer skicka händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="4fcf0-821">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-821">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-822">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-823">Informations fält 2: lagrings-ID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4fcf0-824">Info-fält 3: kod för objekt format.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="4fcf0-825">Info-fält 4: objekt associeras.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="4fcf0-826">Hämtning av partiella objekt data för enhets klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="4fcf0-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="4fcf0-828">**Ikonen** ![ Enhets klass Pima del objekt data hämta ikon](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="4fcf0-829">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-829">**Description**</span></span>

<span data-ttu-id="4fcf0-830">Den här händelsen representerar en USBX enhets klass Pima del objekt data hämta händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="4fcf0-831">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-831">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-832">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-833">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-834">Informations fält 3: offset begärd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="4fcf0-835">Info fält 4: den begärda längden.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="4fcf0-836">Skicka svar för enhets klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="4fcf0-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="4fcf0-838">**Ikonen** ![ Ikon för Pima svars sändning i enhets klass](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="4fcf0-839">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-839">**Description**</span></span>

<span data-ttu-id="4fcf0-840">Den här händelsen representerar en USBX enhets klass Pima sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="4fcf0-841">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-841">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-842">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-843">Info fält 2: svars kod.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="4fcf0-844">Info-fält 3: nummer parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="4fcf0-845">Info-fält 4: Pima-parameter 1.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="4fcf0-846">Enhets klass Pima lagrings-ID skicka</span><span class="sxs-lookup"><span data-stu-id="4fcf0-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="4fcf0-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="4fcf0-848">**Ikonen** ![ Enhets klass Pima lagrings-ID skicka ikon](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="4fcf0-849">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-849">**Description**</span></span>

<span data-ttu-id="4fcf0-850">Den här händelsen representerar en USBX enhets klass Pima Storage ID Send event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="4fcf0-851">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-851">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-852">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-853">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-854">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-855">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="4fcf0-856">Skicka Pima Storage-information i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="4fcf0-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="4fcf0-858">**Ikonen** ![ Enhets klass Pima Storage information skicka ikon](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="4fcf0-859">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-859">**Description**</span></span>

<span data-ttu-id="4fcf0-860">Den här händelsen representerar en USBX enhets klass Pima Storage information send event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="4fcf0-861">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-861">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-862">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-863">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-864">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-865">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="4fcf0-866">Aktivering av enhets klass RNDIS</span><span class="sxs-lookup"><span data-stu-id="4fcf0-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="4fcf0-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="4fcf0-868">**Ikonen** ![ RNDIS Aktivera ikon för enhets klass](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="4fcf0-869">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-869">**Description**</span></span>

<span data-ttu-id="4fcf0-870">Den här händelsen representerar en USBX enhets klass RNDIS aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="4fcf0-871">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-871">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-872">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-873">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-874">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-875">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="4fcf0-876">Inaktive ring av enhets klass RNDIS</span><span class="sxs-lookup"><span data-stu-id="4fcf0-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="4fcf0-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="4fcf0-878">**Ikonen** ![ Ikon för RNDIS för enhets klass](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="4fcf0-879">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-879">**Description**</span></span>

<span data-ttu-id="4fcf0-880">Den här händelsen representerar en USBX enhets klass RNDIS-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-881">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-881">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-882">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-883">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-884">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-885">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="4fcf0-886">Enhets klass RNDIS meddelande Keep Alive</span><span class="sxs-lookup"><span data-stu-id="4fcf0-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="4fcf0-887">ux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="4fcf0-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="4fcf0-888">**Ikonen** ![ Enhets klass RNDIS meddelande ikonen Behåll Alive](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="4fcf0-889">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-889">**Description**</span></span>

<span data-ttu-id="4fcf0-890">Den här händelsen representerar en USBX enhets klass RNDIS meddelande om att händelsen "Keep Alive".</span><span class="sxs-lookup"><span data-stu-id="4fcf0-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="4fcf0-891">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-891">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-892">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-893">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-894">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-895">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="4fcf0-896">RNDIS meddelande fråga för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="4fcf0-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="4fcf0-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="4fcf0-898">**Ikonen** ![ RNDIS meddelande fråga i enhets klass](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="4fcf0-899">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-899">**Description**</span></span>

<span data-ttu-id="4fcf0-900">Den här händelsen representerar en USBX enhets klass RNDIS meddelande händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="4fcf0-901">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-901">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-902">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-903">Info fält 2: RNDIS OID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="4fcf0-904">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-905">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="4fcf0-906">RNDIS meddelande återställning för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="4fcf0-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="4fcf0-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="4fcf0-908">**Ikonen** ![ Ikon för enhets klass RNDIS meddelande återställning](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="4fcf0-909">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-909">**Description**</span></span>

<span data-ttu-id="4fcf0-910">Den här händelsen representerar en USBX enhets klass RNDIS Message rereset-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="4fcf0-911">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-911">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-912">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-913">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-914">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="4fcf0-915">RNDIS meddelande uppsättning för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="4fcf0-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="4fcf0-917">**Ikonen** ![ Enhets klass RNDIS meddelande uppsättnings ikon](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="4fcf0-918">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-918">**Description**</span></span>

<span data-ttu-id="4fcf0-919">Den här händelsen representerar en USBX enhets klass RNDIS meddelande uppsättnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="4fcf0-920">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-920">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-921">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-922">Info fält 2: RNDIS OID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="4fcf0-923">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-924">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="4fcf0-925">Mottagning av enhets klassens RNDIS-paket</span><span class="sxs-lookup"><span data-stu-id="4fcf0-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="4fcf0-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="4fcf0-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="4fcf0-927">**Ikonen** ![ Ikon för enhets klassens RNDIS-paket](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="4fcf0-928">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-928">**Description**</span></span>

<span data-ttu-id="4fcf0-929">Den här händelsen representerar en USBX enhets klass RNDIS Packet Receive-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="4fcf0-930">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-930">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-931">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-932">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-933">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-934">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="4fcf0-935">Överföring av RNDIS-paket i enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="4fcf0-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="4fcf0-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="4fcf0-937">**Ikonen** ![ Enhets klass RNDIS Packet sändnings ikon](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="4fcf0-938">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-938">**Description**</span></span>

<span data-ttu-id="4fcf0-939">Den här händelsen representerar en USBX enhets klass RNDIS Packet sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="4fcf0-940">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-940">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-941">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-942">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-943">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-944">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="4fcf0-945">Aktivera enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="4fcf0-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="4fcf0-947">**Ikonen** ![ Aktiverings ikon för enhets klass lagring](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="4fcf0-948">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-948">**Description**</span></span>

<span data-ttu-id="4fcf0-949">Den här händelsen representerar en händelse för aktivering av USBX enhets klass lagring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="4fcf0-950">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-950">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-951">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-952">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-953">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-954">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="4fcf0-955">Inaktive ring av enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="4fcf0-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="4fcf0-957">**Ikonen** ![ Ikon för enhets klassens lagrings inaktive rad](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="4fcf0-958">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-958">**Description**</span></span>

<span data-ttu-id="4fcf0-959">Den här händelsen representerar en USBX enhets klass lagrings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-960">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-960">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-961">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-962">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-963">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-964">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="4fcf0-965">Lagrings format för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="4fcf0-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="4fcf0-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="4fcf0-967">**Ikonen** ![ Ikon för lagrings format för enhets klass](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="4fcf0-968">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-968">**Description**</span></span>

<span data-ttu-id="4fcf0-969">Den här händelsen representerar ett USBX för enhets klassens lagrings format.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="4fcf0-970">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-970">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-971">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-972">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-973">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-974">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="4fcf0-975">Förfrågan om enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="4fcf0-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="4fcf0-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="4fcf0-977">**Ikonen** ![ Ikon för enhets klass lagrings förfrågan](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="4fcf0-978">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-978">**Description**</span></span>

<span data-ttu-id="4fcf0-979">Den här händelsen representerar en USBX enhets klass lagrings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="4fcf0-980">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-980">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-981">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-982">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-983">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-984">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="4fcf0-985">Val av enhets klassens lagrings läge</span><span class="sxs-lookup"><span data-stu-id="4fcf0-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="4fcf0-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="4fcf0-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="4fcf0-987">**Ikonen** ![ Enhets klassens lagrings läge Välj ikon](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="4fcf0-988">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-988">**Description**</span></span>

<span data-ttu-id="4fcf0-989">Den här händelsen representerar ett USBX enhets klass lagrings läge Välj händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="4fcf0-990">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-990">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-991">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-992">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-993">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-994">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="4fcf0-995">Sense i enhets klassens lagrings läge</span><span class="sxs-lookup"><span data-stu-id="4fcf0-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="4fcf0-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="4fcf0-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="4fcf0-997">**Ikonen** ![ Ikon för lagrings läge i enhets klass](./media/user-guide/usbx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="4fcf0-998">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-998">**Description**</span></span>

<span data-ttu-id="4fcf0-999">Den här händelsen representerar en USBX enhets klass lagrings läges händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="4fcf0-1000">Informations fält</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1000">Information Fields</span></span> 

- <span data-ttu-id="4fcf0-1001">NFO-fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1002">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1003">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1004">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="4fcf0-1005">Enhets klass lagring förhindra borttagning av media</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="4fcf0-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="4fcf0-1007">**Ikonen** ![ Enhets klass lagring förhindra att ikonen borttagning av media](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="4fcf0-1008">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1008">**Description**</span></span>

<span data-ttu-id="4fcf0-1009">Den här händelsen representerar en USBX enhets klass lagring förhindra händelsen borttagning av media.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="4fcf0-1010">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1010">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1011">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1012">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1013">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1014">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="4fcf0-1015">Läsning av enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="4fcf0-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="4fcf0-1017">**Ikonen** ![ Läs ikon för enhets klass lagring](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="4fcf0-1018">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1018">**Description**</span></span>

<span data-ttu-id="4fcf0-1019">Den här händelsen representerar en USBX enhets klass lagrings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="4fcf0-1020">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1020">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1021">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1022">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1023">Informations fält 3: sektor.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="4fcf0-1024">Info fält 4: numrerade sektorer.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="4fcf0-1025">Läs kapacitet för enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="4fcf0-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="4fcf0-1027">**Ikonen** ![ Enhets klass lagring Läs kapacitets ikon](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="4fcf0-1028">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1028">**Description**</span></span>

<span data-ttu-id="4fcf0-1029">Den här händelsen representerar en USBX enhets klass lagrings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="4fcf0-1030">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1030">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1031">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1032">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1033">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1034">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="4fcf0-1035">Kapacitet för Läs format för enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="4fcf0-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="4fcf0-1037">**Ikonen** ![ Kapacitets ikon för Läs format för enhets klass lagring](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="4fcf0-1038">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1038">**Description**</span></span>

<span data-ttu-id="4fcf0-1039">Den här händelsen representerar en USBX för enhets klass lagrings kapacitet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="4fcf0-1040">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1040">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1041">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1042">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1043">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1044">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="4fcf0-1045">Läs innehålls förteckning för enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="4fcf0-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="4fcf0-1047">**Ikonen** ![ Enhets klass lagring läsa innehålls förtecknings ikon](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="4fcf0-1048">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1048">**Description**</span></span>

<span data-ttu-id="4fcf0-1049">Den här händelsen representerar en USBX enhets klass lagring läsa TOC-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="4fcf0-1050">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1050">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1051">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1052">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1053">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1054">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="4fcf0-1055">Sense-begäran för enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="4fcf0-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="4fcf0-1057">**Ikonen** ![ Ikon för enhets klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="4fcf0-1058">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1058">**Description**</span></span>

<span data-ttu-id="4fcf0-1059">Den här händelsen representerar en händelse för en USBX enhets klass lagrings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="4fcf0-1060">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1060">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1061">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1062">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1063">Info-fält 3: Sense-nyckel.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="4fcf0-1064">Info fält 4: kod.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="4fcf0-1065">Start stopp för enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="4fcf0-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="4fcf0-1067">**Ikonen** ![ Start stopps ikon för enhets klass lagring](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="4fcf0-1068">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1068">**Description**</span></span>

<span data-ttu-id="4fcf0-1069">Den här händelsen representerar en USBX enhets klass lagrings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="4fcf0-1070">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1070">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1071">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1072">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1073">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1074">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="4fcf0-1075">Lagrings test för enhets klass klar</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="4fcf0-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="4fcf0-1077">**Ikonen** ![ Ikon för lagrings test för enhets klass](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="4fcf0-1078">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1078">**Description**</span></span>

<span data-ttu-id="4fcf0-1079">Den här händelsen representerar en USBX för enhets klass lagrings test.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="4fcf0-1080">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1080">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1081">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1082">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1083">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1084">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="4fcf0-1085">Verifiera lagring av enhets klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="4fcf0-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="4fcf0-1087">**Ikonen** ![ Enhets klass lagring verifiera ikon](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="4fcf0-1088">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1088">**Description**</span></span>

<span data-ttu-id="4fcf0-1089">Den här händelsen representerar en USBX enhets klass lagring verifiera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="4fcf0-1090">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1090">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1091">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1092">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1093">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1094">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="4fcf0-1095">Skrivning av enhets klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="4fcf0-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="4fcf0-1097">**Ikonen** ![ Skriv ikon för enhets klass lagring](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="4fcf0-1098">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1098">**Description**</span></span>

<span data-ttu-id="4fcf0-1099">Den här händelsen representerar en Skriv händelse för lagring av USBX enhets klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="4fcf0-1100">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1100">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1101">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1102">Info fält 2: LUN.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4fcf0-1103">Informations fält 3: sektor.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="4fcf0-1104">Info fält 4: numrerade sektorer.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="4fcf0-1105">Alternativ inställning för enhets stack Hämta</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="4fcf0-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="4fcf0-1107">**Ikonen** ![ Alternativ inställnings ikon för enhets stack](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="4fcf0-1108">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1108">**Description**</span></span>

<span data-ttu-id="4fcf0-1109">Den här händelsen representerar en alternativ inställnings händelse för USBX Device stack.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="4fcf0-1110">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1110">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1111">Info-fält 1: gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4fcf0-1112">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1113">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1114">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="4fcf0-1115">Alternativ inställnings uppsättning för enhets stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="4fcf0-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="4fcf0-1117">**Ikonen** ![ Ikon för alternativ inställnings uppsättning för enhets stack](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="4fcf0-1118">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1118">**Description**</span></span>

<span data-ttu-id="4fcf0-1119">Den här händelsen representerar en händelse för alternativ inställnings uppsättning för USBX-enhets stack.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="4fcf0-1120">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1120">**Information Fields**</span></span>
- <span data-ttu-id="4fcf0-1121">Info-fält 1: gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4fcf0-1122">Info-fält 2: värde för alternativ inställning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="4fcf0-1123">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1124">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="4fcf0-1125">Enhets Stack klass register</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="4fcf0-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="4fcf0-1127">**Ikonen** ![ Enhets Stack klass register ikon](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="4fcf0-1128">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1128">**Description**</span></span>

<span data-ttu-id="4fcf0-1129">Den här händelsen representerar en USBX enhets Stack klass register händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="4fcf0-1130">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1130">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1131">Informations fält 1: klass namn.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="4fcf0-1132">Informations fält 2: gränssnitts nummer.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="4fcf0-1133">Info-fält 3: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="4fcf0-1134">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="4fcf0-1135">Rensnings funktion för enhets stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="4fcf0-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="4fcf0-1137">**Ikonen** ![ Enhets stack rensa funktions ikon](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="4fcf0-1138">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1138">**Description**</span></span>

<span data-ttu-id="4fcf0-1139">Den här händelsen representerar en USBX enhets stack rensa funktions händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="4fcf0-1140">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1140">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1141">Informations fält 1: typ av begäran.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="4fcf0-1142">Info-fält 2: värde för begäran.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="4fcf0-1143">Informations fält 3: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4fcf0-1144">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="4fcf0-1145">Hämta enhets stack konfiguration</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="4fcf0-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="4fcf0-1147">**Ikonen** ![ Hämta ikon för enhets stack konfiguration](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="4fcf0-1148">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1148">**Description**</span></span>

<span data-ttu-id="4fcf0-1149">Den här händelsen representerar en USBX enhets stack konfiguration Hämta händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="4fcf0-1150">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1150">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1151">Informations fält 1: konfigurations värde.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="4fcf0-1152">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1153">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1154">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="4fcf0-1155">Konfigurations uppsättning för enhets stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="4fcf0-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="4fcf0-1157">**Ikonen** ![ Ikon för enhets stack konfigurations uppsättning](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="4fcf0-1158">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1158">**Description**</span></span>

<span data-ttu-id="4fcf0-1159">Den här händelsen representerar en händelse för konfigurations uppsättning för USBX Device stack-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="4fcf0-1160">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1160">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1161">Informations fält 1: konfigurations värde.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="4fcf0-1162">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1163">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1164">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="4fcf0-1165">Enhets stack anslutning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="4fcf0-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="4fcf0-1167">**Ikonen** ![ Enhets stackens anslutnings ikon](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="4fcf0-1168">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1168">**Description**</span></span>

<span data-ttu-id="4fcf0-1169">Den här händelsen representerar en USBX för enhets stack beskrivning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="4fcf0-1170">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1170">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1171">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4fcf0-1172">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1173">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1174">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="4fcf0-1175">Skicka enhets Stacks Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="4fcf0-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="4fcf0-1177">**Ikonen** ![ Ikon för att skicka enhets stack Beskrivning](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="4fcf0-1178">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1178">**Description**</span></span>

<span data-ttu-id="4fcf0-1179">Den här händelsen representerar en USBX för enhets stack beskrivning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="4fcf0-1180">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1180">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1181">Informations fält 1: beskrivnings typ.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="4fcf0-1182">Informations fält 2: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4fcf0-1183">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1184">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="4fcf0-1185">Enhets stack från koppling</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="4fcf0-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="4fcf0-1187">**Ikonen** ![ Ikon för enhets stack från koppling](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="4fcf0-1188">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1188">**Description**</span></span>

<span data-ttu-id="4fcf0-1189">Den här händelsen representerar en händelse för USBX enhets stack från koppling.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="4fcf0-1190">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1190">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1191">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-1192">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1193">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1194">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="4fcf0-1195">Enhets stackens slut punkt bås</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="4fcf0-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="4fcf0-1197">**Ikonen** ![ Ikon för enhets stackens slut punkts bås](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="4fcf0-1198">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1198">**Description**</span></span>

<span data-ttu-id="4fcf0-1199">Den här händelsen representerar en händelse för USBX Device stack Endpoint bås.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="4fcf0-1200">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1200">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1201">Informations fält 1: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-1202">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1203">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1204">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="4fcf0-1205">Hämta status för enhets stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="4fcf0-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="4fcf0-1207">**Ikonen** ![ Enhets stack Hämta status ikon](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="4fcf0-1208">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1208">**Description**</span></span>

<span data-ttu-id="4fcf0-1209">Den här händelsen representerar en USBX enhets stack Hämta status händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="4fcf0-1210">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1210">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1211">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4fcf0-1212">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1213">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1214">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="4fcf0-1215">Aktivering av enhets stack värd</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="4fcf0-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="4fcf0-1217">**Ikonen** ![ Aktiverings ikon för värd för enhets stack](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="4fcf0-1218">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1218">**Description**</span></span>

<span data-ttu-id="4fcf0-1219">Den här händelsen representerar en aktiverings händelse för USBX Device stack-värden.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="4fcf0-1220">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1220">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1221">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4fcf0-1222">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1223">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1224">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="4fcf0-1225">Initiera enhets stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="4fcf0-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="4fcf0-1227">**Ikonen** ![ Ikon för enhets stack initierare](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="4fcf0-1228">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1228">**Description**</span></span>

<span data-ttu-id="4fcf0-1229">Den här händelsen representerar en händelse för initiering av USBX enhets stack.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="4fcf0-1230">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1230">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1231">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4fcf0-1232">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1233">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1234">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="4fcf0-1235">Ta bort enhets Stacks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="4fcf0-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="4fcf0-1237">**Ikonen** ![ Borttagnings ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="4fcf0-1238">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1238">**Description**</span></span>

<span data-ttu-id="4fcf0-1239">Den här händelsen representerar en händelse för borttagning av USBX Device stack-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="4fcf0-1240">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1240">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1241">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-1242">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1243">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1244">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="4fcf0-1245">Hämta enhets stack gränssnitt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="4fcf0-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="4fcf0-1247">**Ikonen** ![ Hämta ikon för enhets stackens gränssnitt](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="4fcf0-1248">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1248">**Description**</span></span>

<span data-ttu-id="4fcf0-1249">Den här händelsen representerar en händelse för hämtning av USBX Device stack-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="4fcf0-1250">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1250">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1251">Info-fält 1: gränssnitts värde.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4fcf0-1252">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1253">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1254">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="4fcf0-1255">Enhets stack gränssnitts uppsättning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="4fcf0-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="4fcf0-1257">**Ikonen** ![ Ikon för enhets stackens gränssnitts uppsättning](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="4fcf0-1258">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1258">**Description**</span></span>

<span data-ttu-id="4fcf0-1259">Den här händelsen representerar en händelse för en USBX enhets stack gränssnitts uppsättning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="4fcf0-1260">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1260">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1261">Informations fält 1: värde för begäran.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="4fcf0-1262">Informations fält 2: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4fcf0-1263">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1264">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="4fcf0-1265">Enhets stack uppsättnings funktion</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="4fcf0-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="4fcf0-1267">**Ikonen** ![ Funktions ikon för enhets stack uppsättning](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="4fcf0-1268">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1268">**Description**</span></span>

<span data-ttu-id="4fcf0-1269">Den här händelsen representerar en funktions händelse för en USBX enhets stack uppsättning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="4fcf0-1270">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1270">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1271">Informations fält 1: värde för begäran.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="4fcf0-1272">Informations fält 2: begär index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4fcf0-1273">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1274">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="4fcf0-1275">Avbryt enhets stack överföring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="4fcf0-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="4fcf0-1277">**Ikonen** ![ Avbrotts ikon för enhets stack överföring](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="4fcf0-1278">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1278">**Description**</span></span>

<span data-ttu-id="4fcf0-1279">Den här händelsen representerar en avbrotts händelse för USBX Device stack-överföring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="4fcf0-1280">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1280">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1281">Informations fält 1: överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="4fcf0-1282">Info fält 2: slut för ande kod.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="4fcf0-1283">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1284">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="4fcf0-1285">Enhets stack överför alla begäran om att avbryta begäran</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="4fcf0-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="4fcf0-1287">**Ikonen** ![ Ikon för enhets stacken överför alla begär Anden](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="4fcf0-1288">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1288">**Description**</span></span>

<span data-ttu-id="4fcf0-1289">Den här händelsen representerar en USBX Device stack-överföring alla begär Anden om att avbryta begäran.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="4fcf0-1290">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1290">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1291">Informations fält 1: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-1292">Info fält 2: slut för ande kod.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="4fcf0-1293">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1294">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="4fcf0-1295">Begäran om enhets stack överföring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="4fcf0-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="4fcf0-1297">**Ikonen** ![ Ikon för begäran om enhets stack-överföring](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="4fcf0-1298">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1298">**Description**</span></span>

<span data-ttu-id="4fcf0-1299">Den här händelsen representerar en begäran om USBX enhets stack-överföring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="4fcf0-1300">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1300">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1301">Informations fält 1: överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="4fcf0-1302">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1303">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1304">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="4fcf0-1305">Aktivering av värd klass Asix</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="4fcf0-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="4fcf0-1307">**Ikonen** ![ Asix Aktivera ikon för värd klass](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="4fcf0-1308">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1308">**Description**</span></span>

<span data-ttu-id="4fcf0-1309">Den här händelsen representerar en USBX-Asix för värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="4fcf0-1310">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1310">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1311">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1312">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1313">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1314">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="4fcf0-1315">Asix inaktive ring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="4fcf0-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="4fcf0-1317">**Ikonen** ![ Asix-ikon för värd klass](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="4fcf0-1318">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1318">**Description**</span></span>

<span data-ttu-id="4fcf0-1319">Den här händelsen representerar en USBX värd klass Asix-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1320">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1320">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1321">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1322">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1323">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1324">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="4fcf0-1325">Avbrotts meddelande för värd klass Asix</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="4fcf0-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="4fcf0-1327">**Ikonen** ![ Asix för värd klassens avbrotts meddelande](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="4fcf0-1328">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1328">**Description**</span></span>

<span data-ttu-id="4fcf0-1329">Den här händelsen representerar en USBX Asix-avbrotts meddelande händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="4fcf0-1330">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1330">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1331">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-1332">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1333">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1334">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="4fcf0-1335">Läsning av värd klass Asix</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="4fcf0-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="4fcf0-1337">**Ikonen** ![ Läs ikon för värd klassen Asix](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="4fcf0-1338">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1338">**Description**</span></span>

<span data-ttu-id="4fcf0-1339">Den här händelsen representerar en USBX värd klass Asix Read event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="4fcf0-1340">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1340">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1341">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1342">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1343">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-1344">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="4fcf0-1345">Skrivning av värd klass Asix</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="4fcf0-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="4fcf0-1347">**Ikonen** ![ Asix Skriv ikon för värd klass](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="4fcf0-1348">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1348">**Description**</span></span>

<span data-ttu-id="4fcf0-1349">Den här händelsen representerar en USBX Asix Skriv händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="4fcf0-1350">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1350">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1351">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1352">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1353">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-1354">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="4fcf0-1355">Aktivera ljud för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="4fcf0-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="4fcf0-1357">**Ikonen** ![ Ikon för ljud aktivering i värd klass](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="4fcf0-1358">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1358">**Description**</span></span>

<span data-ttu-id="4fcf0-1359">Den här händelsen representerar en USBX-händelse för värd klass ljud.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="4fcf0-1360">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1360">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1361">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1362">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1363">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1364">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="4fcf0-1365">Hämta ljud kontroll värde för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="4fcf0-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="4fcf0-1367">**Ikonen** ![ Ikonen Hämta ljud kontroll värde i värd klass](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="4fcf0-1368">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1368">**Description**</span></span>

<span data-ttu-id="4fcf0-1369">Den här händelsen representerar en händelse för ett ljud kontroll värde i USBX Host-klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="4fcf0-1370">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1370">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1371">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1372">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1373">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1374">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="4fcf0-1375">Värde uppsättning för ljud kontroll i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="4fcf0-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="4fcf0-1377">**Ikonen** ![ Ikon för ljud kontroll värde för värd klass](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="4fcf0-1378">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1378">**Description**</span></span>

<span data-ttu-id="4fcf0-1379">Den här händelsen representerar en intern NetX I/O-drivrutin som Uppskjut bearbetnings händelsen.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="4fcf0-1380">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1380">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1381">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1382">Info-fält 2: ljud kontroll.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="4fcf0-1383">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1384">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="4fcf0-1385">Ljud inaktive ring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="4fcf0-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="4fcf0-1387">**Ikonen** ![ Ikon för ljud inaktive ring av värd klass](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="4fcf0-1388">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1388">**Description**</span></span>

<span data-ttu-id="4fcf0-1389">Den här händelsen representerar en ljud inaktive rings händelse för USBX värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1390">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1390">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1391">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1392">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1393">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1394">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="4fcf0-1395">Ljud läsning av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="4fcf0-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="4fcf0-1397">**Ikonen** ![ Ljud läsnings ikon för värd klass](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="4fcf0-1398">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1398">**Description**</span></span>

<span data-ttu-id="4fcf0-1399">Den här händelsen representerar en USBX för ljud läsnings händelse för värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="4fcf0-1400">Informations fält</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1400">Information Fields</span></span> 
- <span data-ttu-id="4fcf0-1401">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1402">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1403">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-1404">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="4fcf0-1405">Ljud uppspelning av värd klass, samplings hämtning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="4fcf0-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="4fcf0-1407">**Ikonen** ![ Exempel på hämtnings ikon för värd klassens ljud strömning](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="4fcf0-1408">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1408">**Description**</span></span>

<span data-ttu-id="4fcf0-1409">Den här händelsen representerar en USBX för värd klass för ljud uppspelning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="4fcf0-1410">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1410">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1411">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1412">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1413">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1414">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="4fcf0-1415">Samplings uppsättning för värd klassens ljud strömning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="4fcf0-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="4fcf0-1417">**Ikonen** ![ Ikon för samplings uppsättning för värd klassens ljud strömning](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="4fcf0-1418">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1418">**Description**</span></span>

<span data-ttu-id="4fcf0-1419">Den här händelsen representerar en insamlings händelse för ljud strömning i USBX Host Class.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="4fcf0-1420">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1420">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1421">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1422">Info fält 2: ljud sampling.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="4fcf0-1423">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1424">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="4fcf0-1425">Ljud skrivning för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="4fcf0-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="4fcf0-1427">**Ikonen** ![ Ljud Skriv ikon för värd klass](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="4fcf0-1428">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1428">**Description**</span></span>

<span data-ttu-id="4fcf0-1429">Den här händelsen representerar en ljud skrivnings händelse för en USBX värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="4fcf0-1430">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1430">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1431">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1432">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1433">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-1434">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="4fcf0-1435">Värd klass CDC-ACM aktivera</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="4fcf0-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="4fcf0-1437">**Ikonen** ![ Värd klass C D C A C M Aktivera ikon](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="4fcf0-1438">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1438">**Description**</span></span>

<span data-ttu-id="4fcf0-1439">Den här händelsen representerar en USBX-värd klass CDC ACM aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="4fcf0-1440">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1440">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1441">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1442">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1443">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1444">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="4fcf0-1445">Värd klass CDC ACM-inaktive ring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="4fcf0-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="4fcf0-1447">**Ikonen** ![ Värd klass C D C A C M inaktivera ikon](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="4fcf0-1448">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1448">**Description**</span></span>

<span data-ttu-id="4fcf0-1449">Den här händelsen representerar en USBX-värd klass CDC ACM-händelsen.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1450">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1450">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1451">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1452">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1453">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1454">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="4fcf0-1455">Värd klass CDC ACM IOCTL abort i pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="4fcf0-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="4fcf0-1457">**Ikonen** ![ Värd klass C D C A C M I O C T L avbryter i pipe-ikonen](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="4fcf0-1458">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1458">**Description**</span></span>

<span data-ttu-id="4fcf0-1459">Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL abort i pipe-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="4fcf0-1460">Informations fält</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1460">Information Fields</span></span> 

- <span data-ttu-id="4fcf0-1461">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1462">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-1463">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1464">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="4fcf0-1465">Värd klass CDC ACM IOCTL avbryter pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="4fcf0-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="4fcf0-1467">**Ikon** ! [[Värd klass C D c A c M I O c T L ta bort pipe-ikon](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="4fcf0-1468">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1468">**Description**</span></span>

<span data-ttu-id="4fcf0-1469">Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL avbryter pipe-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="4fcf0-1470">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1470">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1471">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1472">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-1473">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1474">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="4fcf0-1475">Värd klass CDC ACM IOCTL Hämta enhets status</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="4fcf0-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="4fcf0-1477">**Ikonen** ![ Värd klass C D C A C M I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="4fcf0-1478">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1478">**Description**</span></span>

<span data-ttu-id="4fcf0-1479">Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL get enhets status händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="4fcf0-1480">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1480">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1481">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1482">Info fält 2: enhets status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="4fcf0-1483">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1484">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="4fcf0-1485">Värd klass CDC ACM IOCTL get line-kodning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="4fcf0-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="4fcf0-1487">**Ikonen** ![ Värd klass C D C A C M I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="4fcf0-1488">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1488">**Description**</span></span>

<span data-ttu-id="4fcf0-1489">Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL get line kodnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="4fcf0-1490">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1490">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1491">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1492">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-1493">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1494">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="4fcf0-1495">Återanrop för värd klass CDC ACM IOCTL-meddelande</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="4fcf0-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="4fcf0-1497">**Ikonen** ![ Värd klass C D C A C M I O C T L ikon för återanrop i meddelande](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="4fcf0-1498">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1498">**Description**</span></span>

<span data-ttu-id="4fcf0-1499">Den här händelsen representerar en USBX för värd klass CDC ACM IOCTL-meddelande.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="4fcf0-1500">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1500">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1501">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1502">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-1503">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1504">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="4fcf0-1505">Värd klass CDC ACM IOCTL skicka rast</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="4fcf0-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="4fcf0-1507">**Ikonen** ![ Värd klass C D C A C M I O C T L-ikonen skicka rast](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="4fcf0-1508">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1508">**Description**</span></span>

<span data-ttu-id="4fcf0-1509">Den här händelsen representerar en USBX-värd klass CDC ACM IOCTL Send Break event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="4fcf0-1510">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1510">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1511">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1512">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-1513">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1514">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="4fcf0-1515">Värd klass CDC ACM IOCTL set line-kodning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="4fcf0-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="4fcf0-1517">**Ikonen** ![ Värd klass C D C A C M I O C T L v Ange ikon ikon för linje kodning ](./media/user-guide/usbx-events/image97.png) ] (./media/user-guide/usbx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="4fcf0-1518">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1518">**Description**</span></span>

<span data-ttu-id="4fcf0-1519">Den här händelsen representerar en USBX för värd klass CDC ACM IOCTL som anger linje kodning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="4fcf0-1520">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1520">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1521">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1522">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-1523">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1524">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="4fcf0-1525">Värd klass CDC ACM IOCTL ange linje status</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="4fcf0-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="4fcf0-1527">**Ikonen** ![ Värd klass C D C A C M I O C T L ikon för ange linje tillstånd](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="4fcf0-1528">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1528">**Description**</span></span>

<span data-ttu-id="4fcf0-1529">Den här händelsen representerar en USBX värd klass CDC ACM IOCTL set line State event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="4fcf0-1530">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1530">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1531">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1532">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-1533">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1534">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="4fcf0-1535">Värd klass CDC ACM Read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="4fcf0-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="4fcf0-1537">**Ikonen** ![ Värd klass C D A C M Läs ikon](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="4fcf0-1538">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1538">**Description**</span></span>

<span data-ttu-id="4fcf0-1539">Den här händelsen representerar en USBX-värd klass CDC ACM Read event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="4fcf0-1540">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1540">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1541">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1542">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1543">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="4fcf0-1544">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="4fcf0-1545">Start av värd klassens CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="4fcf0-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="4fcf0-1547">**Ikonen** ![ Start ikon för värd klass C D A C M](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="4fcf0-1548">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1548">**Description**</span></span>

<span data-ttu-id="4fcf0-1549">Den här händelsen representerar start händelsen för en USBX-värd klass CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="4fcf0-1550">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1550">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1551">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1552">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1553">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1554">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="4fcf0-1555">Stopp för värd klass CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="4fcf0-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="4fcf0-1557">**Ikonen** ![ Svars ikon för värd klass C D A C M](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="4fcf0-1558">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1558">**Description**</span></span>

<span data-ttu-id="4fcf0-1559">Den här händelsen representerar en USBX för värd klass CDC ACM.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="4fcf0-1560">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1560">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1561">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1562">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1563">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="4fcf0-1564">Värd klass CDC ACM-skrivning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="4fcf0-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="4fcf0-1566">**Ikonen** ![ Värd klass C D A C M Skriv ikon](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="4fcf0-1567">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1567">**Description**</span></span>

<span data-ttu-id="4fcf0-1568">Den här händelsen representerar en USBX värd klass CDC ACM Write event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="4fcf0-1569">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1569">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1570">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1571">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1572">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="4fcf0-1573">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="4fcf0-1574">Aktivering av värd klass Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="4fcf0-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="4fcf0-1576">**Ikonen** ![ Dpump Aktivera ikon för värd klass](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="4fcf0-1577">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1577">**Description**</span></span>

<span data-ttu-id="4fcf0-1578">Den här händelsen representerar en USBX-Dpump aktiverings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="4fcf0-1579">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1579">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1580">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1581">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1582">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1583">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="4fcf0-1584">Dpump inaktive ring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="4fcf0-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="4fcf0-1586">**Ikonen** ![ Dpump-ikon för värd klass](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="4fcf0-1587">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1587">**Description**</span></span>

<span data-ttu-id="4fcf0-1588">Den här händelsen representerar en USBX värd klass Dpump-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1589">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1589">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1590">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1591">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1592">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1593">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="4fcf0-1594">Läsning av värd klass Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="4fcf0-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="4fcf0-1596">**Ikonen** ![ Läs ikon för värd klassen Dpump](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="4fcf0-1597">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1597">**Description**</span></span>

<span data-ttu-id="4fcf0-1598">Den här händelsen representerar en USBX värd klass Dpump Read event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="4fcf0-1599">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1599">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1600">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1601">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1602">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-1603">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="4fcf0-1604">Skrivning av värd klass Dpump</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="4fcf0-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="4fcf0-1606">**Ikonen** ![ Dpump Skriv ikon för värd klass](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="4fcf0-1607">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1607">**Description**</span></span>

<span data-ttu-id="4fcf0-1608">Den här händelsen representerar en USBX Dpump Skriv händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="4fcf0-1609">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1609">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1610">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1611">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1612">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-1613">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="4fcf0-1614">HID-aktivering för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="4fcf0-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="4fcf0-1616">**Ikonen** ![ Ikon för HID-aktivering i värd klass](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="4fcf0-1617">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1617">**Description**</span></span>

<span data-ttu-id="4fcf0-1618">Den här händelsen representerar en HID-USBX för värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="4fcf0-1619">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1619">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1620">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1621">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1622">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1623">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="4fcf0-1624">HID-klient register för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="4fcf0-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="4fcf0-1626">**Ikonen** ![ Register ikon för HID-klient för värd klass](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="4fcf0-1627">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1627">**Description**</span></span>

<span data-ttu-id="4fcf0-1628">Den här händelsen representerar en USBX-händelse för HID-klient för värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="4fcf0-1629">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1629">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1630">Informations fält 1: HID-klientcertifikat.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="4fcf0-1631">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1632">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1633">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="4fcf0-1634">HID-inaktive ring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="4fcf0-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="4fcf0-1636">**Ikonen** ![ Ikon för HID-inaktivera värd klass](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="4fcf0-1637">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1637">**Description**</span></span>

<span data-ttu-id="4fcf0-1638">Den här händelsen representerar en händelse för HID-inaktive ring av USBX värd klasser.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1639">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1639">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1640">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1641">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1642">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1643">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="4fcf0-1644">HID-inaktivitet i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="4fcf0-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="4fcf0-1646">**Ikonen** ![ Ikon för HID-inaktivitet i värd klass](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="4fcf0-1647">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1647">**Description**</span></span>

<span data-ttu-id="4fcf0-1648">Den här händelsen representerar en USBX-värd klass HID inaktiv get-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="4fcf0-1649">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1649">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1650">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1651">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1652">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1653">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="4fcf0-1654">HID inaktive rad värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="4fcf0-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="4fcf0-1656">**Ikonen** ![ Ikon för HID inaktive rad värd klass](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="4fcf0-1657">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1657">**Description**</span></span>

<span data-ttu-id="4fcf0-1658">Den här händelsen representerar en händelse för HID inaktive rad USBX-värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="4fcf0-1659">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1659">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1660">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1661">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1662">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1663">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="4fcf0-1664">Aktivera HID-tangentbord för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="4fcf0-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="4fcf0-1666">**Ikonen** ![ Ikon för HID-tangentbordet för värd klass](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="4fcf0-1667">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1667">**Description**</span></span>

<span data-ttu-id="4fcf0-1668">Den här händelsen representerar en USBX-värd klass HID tangent bord aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="4fcf0-1669">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1669">**Information Fields**</span></span>
<p><span data-ttu-id="4fcf0-1670">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="4fcf0-1671">Info-fält 2: HID-klient instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="4fcf0-1672">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="4fcf0-1673">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="4fcf0-1674">HID-tangent bords inaktive ring för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="4fcf0-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="4fcf0-1676">**Ikonen** ![ Ikonen värd klass HID tangent bords inaktive ring](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="4fcf0-1677">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1677">**Description**</span></span>

<span data-ttu-id="4fcf0-1678">Den här händelsen representerar en händelse för HID-tangentbordet för USBX-värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1679">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1679">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1680">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1681">Info-fält 2: HID-klient instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4fcf0-1682">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1683">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="4fcf0-1684">Aktivera HID-mus för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="4fcf0-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="4fcf0-1686">**Ikonen** ![ Aktivera ikon för HID-mus i värd klass](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="4fcf0-1687">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1687">**Description**</span></span>

<span data-ttu-id="4fcf0-1688">Den här händelsen representerar en USBX-värd klass HID-mus aktivera händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="4fcf0-1689">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1689">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1690">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1691">Info-fält 2: HID-klient instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4fcf0-1692">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1693">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="4fcf0-1694">Inaktive ring av värd klass HID-mus</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="4fcf0-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="4fcf0-1696">**Ikonen** ![ Värd klass HID-mus inaktivera ikon](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="4fcf0-1697">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1697">**Description**</span></span>

- <span data-ttu-id="4fcf0-1698">Den här händelsen representerar en USBX-värd klass HID-mus.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1699">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1699">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1700">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1701">Info-fält 2: HID-klient instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4fcf0-1702">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1703">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="4fcf0-1704">Aktivera HID-fjärrstyrning av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="4fcf0-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="4fcf0-1706">**Ikonen** ![ Ikonen aktivera HID-fjärrstyrning i värd klass](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="4fcf0-1707">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1707">**Description**</span></span>

<span data-ttu-id="4fcf0-1708">Den här händelsen representerar en USBX-värd klass HID-fjärrstyrning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="4fcf0-1709">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1709">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1710">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1711">Info-fält 2: HID-klient instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4fcf0-1712">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1713">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="4fcf0-1714">HID-fjärrstyrning inaktive ras för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="4fcf0-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="4fcf0-1716">**Ikonen** ![ Ikon för HID-fjärrstyrning av värd klass](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="4fcf0-1717">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1717">**Description**</span></span>

<span data-ttu-id="4fcf0-1718">Den här händelsen representerar en USBX-värd klass HID-fjärrstyrning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1719">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1719">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1720">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1721">Info-fält 2: HID-klient instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4fcf0-1722">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1723">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="4fcf0-1724">Hämta HID-rapport för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="4fcf0-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="4fcf0-1726">**Ikonen** ![ Ikon för Hämta värd klass HID-rapport](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="4fcf0-1727">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1727">**Description**</span></span>

<span data-ttu-id="4fcf0-1728">Den här händelsen representerar en HID-rapport för USBX-värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="4fcf0-1729">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1729">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1730">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1731">Info-fält 2: klient rapport.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="4fcf0-1732">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1733">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="4fcf0-1734">HID-rapport uppsättning för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="4fcf0-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="4fcf0-1736">**Ikonen** ![ Ikon för HID-rapport för värd klass](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="4fcf0-1737">**Beskrivning** Den här händelsen representerar en HID-rapport uppsättning för USBX-värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="4fcf0-1738">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1738">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1739">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1740">Info-fält 2: klient rapport.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="4fcf0-1741">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1742">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="4fcf0-1743">Aktivera värd klass hubb</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="4fcf0-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="4fcf0-1745">**Ikonen** ![ Aktivera ikon för värd klassens hubb](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="4fcf0-1746">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1746">**Description**</span></span>

<span data-ttu-id="4fcf0-1747">Den här händelsen representerar en aktiverings händelse för USBX Host Class Hub.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="4fcf0-1748">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1748">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-1749">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1750">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1751">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1752">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="4fcf0-1753">Identifiera ändring av värd klassens hubb</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="4fcf0-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="4fcf0-1755">**Ikonen** ![ Identifiera ikon för värd klassens hubb ändring](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="4fcf0-1756">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1756">**Description**</span></span>

<span data-ttu-id="4fcf0-1757">Den här händelsen representerar en händelse för att identifiera en USBX för värd klass ändringar.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="4fcf0-1758">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1758">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1759">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1760">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1761">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1762">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="4fcf0-1763">Inaktive ring av värd Klasss hubb</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="4fcf0-1764">ux_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="4fcf0-1765">**Ikonen** ![ Ikonen inaktivera ikon för värd klassens hubb](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="4fcf0-1766">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1766">**Description**</span></span>

<span data-ttu-id="4fcf0-1767">Den här händelsen representerar en USBX-händelse för värd klassens hubb.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1768">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1768">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1769">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1770">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1771">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1772">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="4fcf0-1773">Anslutnings processen för värd klassens hubb port ändring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="4fcf0-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="4fcf0-1775">**Ikonen** ![ Ikon för att ändra anslutnings process för värd klassens hubb port](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="4fcf0-1776">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1776">**Description**</span></span>

<span data-ttu-id="4fcf0-1777">Den här händelsen representerar en USBX anslutnings process händelse för värd klassens hubb.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="4fcf0-1778">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1778">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1779">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1780">Info fält 2: port.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="4fcf0-1781">Info-fält 3: port status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4fcf0-1782">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="4fcf0-1783">Aktiverings processen för värd klassens Hubbs port ändring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="4fcf0-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="4fcf0-1785">**Ikonen** ![ Aktivera process ikon för värd klassens hubb port ändring](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="4fcf0-1786">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1786">**Description**</span></span>

<span data-ttu-id="4fcf0-1787">Den här händelsen representerar en USBX för värd Klasss Hub-port ändra Aktivera process händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="4fcf0-1788">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1788">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1789">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1790">Info fält 2: port.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="4fcf0-1791">Info-fält 3: port status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4fcf0-1792">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="4fcf0-1793">Port ändring i värd klassens hubb över den aktuella processen</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="4fcf0-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="4fcf0-1795">**Ikonen** ![ Port ändring över ikon för värd Klasss hubb över den aktuella process ikonen](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="4fcf0-1796">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1796">**Description**</span></span>

<span data-ttu-id="4fcf0-1797">Den här händelsen representerar att allokera ett paket via nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="4fcf0-1798">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1798">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1799">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1800">Info fält 2: port.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="4fcf0-1801">Info-fält 3: port status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4fcf0-1802">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="4fcf0-1803">Återställnings process för port ändring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="4fcf0-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="4fcf0-1805">**Ikonen** ![ Ikon för ändrings process för värd klassens Hubbs port](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="4fcf0-1806">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1806">**Description**</span></span>

<span data-ttu-id="4fcf0-1807">Den här händelsen representerar en USBX för värd klass för värde ändrings återställning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="4fcf0-1808">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1808">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1809">Informations fält 1: hubb.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="4fcf0-1810">Info fält 2: port.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="4fcf0-1811">Info-fält 3: port status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4fcf0-1812">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="4fcf0-1813">Inaktive ring av värd klassens hubb port ändring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="4fcf0-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="4fcf0-1815">**Ikonen** ![ Ikon för att inaktivera process klassens hubb port ändring](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="4fcf0-1816">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1816">**Description**</span></span>

<span data-ttu-id="4fcf0-1817">Den här händelsen representerar en inaktive ring av en USBX för värd Klasss port ändring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="4fcf0-1818">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1818">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1819">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1820">Info fält 2: port.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="4fcf0-1821">Info-fält 3: port status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4fcf0-1822">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="4fcf0-1823">Aktivering av värd klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="4fcf0-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="4fcf0-1825">**Ikonen** ![ Pima Aktivera ikon för värd klass](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="4fcf0-1826">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1826">**Description**</span></span>

<span data-ttu-id="4fcf0-1827">Den här händelsen representerar en USBX-Pima aktiverings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="4fcf0-1828">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1828">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1829">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1830">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1831">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1832">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="4fcf0-1833">Pima inaktive ring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="4fcf0-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="4fcf0-1835">**Ikonen** ![ Pima-ikon för värd klass](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="4fcf0-1836">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1836">**Description**</span></span>

<span data-ttu-id="4fcf0-1837">Den här händelsen representerar en USBX värd klass Pima-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-1838">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1838">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1839">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1840">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1841">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1842">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="4fcf0-1843">Hämta Pima enhets information för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="4fcf0-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="4fcf0-1845">**Ikonen** ![ Hämta ikon för värd klassens Pima enhets information](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="4fcf0-1846">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1846">**Description**</span></span>

<span data-ttu-id="4fcf0-1847">Den här händelsen representerar en USBX Pima Device information get-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="4fcf0-1848">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1848">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1849">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1850">Info fält 2: Pima-enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="4fcf0-1851">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1852">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="4fcf0-1853">Återställning av värd klass Pima enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="4fcf0-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="4fcf0-1855">**Ikonen** ![ Enhets återställnings ikon för värd klass Pima](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="4fcf0-1856">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1856">**Description**</span></span>

<span data-ttu-id="4fcf0-1857">Den här händelsen representerar en USBX Pima Device rereset-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="4fcf0-1858">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1858">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1859">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1860">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1861">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1862">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="4fcf0-1863">Pima-meddelande för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="4fcf0-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="4fcf0-1865">**Ikonen** ![ Meddelande ikon för värd klass Pima](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="4fcf0-1866">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1866">**Description**</span></span>

<span data-ttu-id="4fcf0-1867">Den här händelsen representerar en USBX-meddelande händelse för värd klass Pima.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="4fcf0-1868">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1868">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1869">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="4fcf0-1870">Info fält 2: händelse kod.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="4fcf0-1871">Info-fält 3: transaktions-ID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="4fcf0-1872">Info fält 4: Parameter1.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="4fcf0-1873">Hämta Pima nummer objekt för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="4fcf0-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="4fcf0-1875">**Ikonen** ![ Ikon för Pima för värd klassens antal objekt](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="4fcf0-1876">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1876">**Description**</span></span>

<span data-ttu-id="4fcf0-1877">Den här händelsen representerar en händelse för en USBX-värd klass Pima Number Objects.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="4fcf0-1878">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1878">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1879">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1880">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1881">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1882">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="4fcf0-1883">Pima objekt stängning i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="4fcf0-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="4fcf0-1885">**Ikonen** ![ Ikonen Stäng Pima objekt i värd klass](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="4fcf0-1886">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1886">**Description**</span></span>

<span data-ttu-id="4fcf0-1887">Den här händelsen representerar händelsen stängning av USBX Pima objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="4fcf0-1888">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1888">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1889">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1890">Info-fält 2: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="4fcf0-1891">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1892">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="4fcf0-1893">Pima objekt kopia av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="4fcf0-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="4fcf0-1895">**Ikonen** ![ Objekt kopierings ikon för värd klass Pima](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="4fcf0-1896">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1896">**Description**</span></span>

<span data-ttu-id="4fcf0-1897">Den här händelsen representerar en USBX Pima objekt kopierings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="4fcf0-1898">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1898">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1899">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1900">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-1901">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1902">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="4fcf0-1903">Ta bort värd klass Pima objekt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="4fcf0-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="4fcf0-1905">**Ikonen** ![ Pima objekt borttagnings ikon för värd klass](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="4fcf0-1906">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1906">**Description**</span></span>

<span data-ttu-id="4fcf0-1907">Den här händelsen representerar en USBX Pima objekt borttagnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="4fcf0-1908">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1908">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1909">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1910">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-1911">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1912">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="4fcf0-1913">Hämta Pima-objekt för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="4fcf0-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="4fcf0-1915">**Ikonen** ![ Pima objekt Hämta ikon för värd klass](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="4fcf0-1916">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1916">**Description**</span></span>

<span data-ttu-id="4fcf0-1917">Den här händelsen representerar att hämta RARP-information via nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="4fcf0-1918">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1918">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1919">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1920">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-1921">Info-fält 3: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="4fcf0-1922">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="4fcf0-1923">Hämta Pima objekt information för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="4fcf0-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="4fcf0-1925">**Ikonen** ![ Hämta ikon för värd klassens Pima objekt information](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="4fcf0-1926">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1926">**Description**</span></span>

<span data-ttu-id="4fcf0-1927">Den här händelsen representerar en USBX-händelse för värd klass Pima objekt information.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="4fcf0-1928">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1928">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1929">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1930">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-1931">Info-fält 3: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="4fcf0-1932">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="4fcf0-1933">Skicka Pima objekt information i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="4fcf0-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="4fcf0-1935">**Ikonen** ![ Skicka ikon för Pima objekt information i värd klass](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="4fcf0-1936">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1936">**Description**</span></span>

<span data-ttu-id="4fcf0-1937">Den här händelsen representerar sändnings händelsen för en USBX-Pima objekt information.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="4fcf0-1938">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1938">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1939">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1940">Info-fält 2: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="4fcf0-1941">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1942">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="4fcf0-1943">Flytt av Pima objekt i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="4fcf0-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="4fcf0-1945">**Ikonen** ![ Ikon för flytt av Pima objekt i värd klass](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="4fcf0-1946">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1946">**Description**</span></span>

<span data-ttu-id="4fcf0-1947">Den här Event reprThis-händelsen representerar en USBX för värd klass Pima objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="4fcf0-1948">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1948">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1949">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1950">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-1951">Info-fält 3: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="4fcf0-1952">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="4fcf0-1953">Skicka Pima objekt i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="4fcf0-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="4fcf0-1955">**Ikonen** ![ Ikon för att skicka Pima objekt i värd klass](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="4fcf0-1956">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1956">**Description**</span></span>

<span data-ttu-id="4fcf0-1957">Den här händelsen representerar en USBX-Pima objekt sändnings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="4fcf0-1958">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1958">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1959">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1960">Info-fält 2: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="4fcf0-1961">Info-fält 3: objektets buffert.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="4fcf0-1962">Info-fält 4: objekt längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="4fcf0-1963">Avbrytning av Pima objekt överföring i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="4fcf0-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="4fcf0-1965">**Ikonen** ![ Avbrotts ikon för Pima objekt överföring i värd klass](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="4fcf0-1966">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1966">**Description**</span></span>

<span data-ttu-id="4fcf0-1967">Den här händelsen representerar en avbrotts händelse för USBX av värd klass Pima objekt överföring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="4fcf0-1968">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1968">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1969">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1970">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-1971">Info-fält 3: objekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="4fcf0-1972">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="4fcf0-1973">Läsning av värd klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="4fcf0-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="4fcf0-1975">**Ikonen** ![ Läs ikon för värd klassen Pima](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="4fcf0-1976">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1976">**Description**</span></span>

<span data-ttu-id="4fcf0-1977">Den här händelsen representerar en USBX värd klass Pima Read event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="4fcf0-1978">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1978">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1979">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1980">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-1981">Informations fält 3: data längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="4fcf0-1982">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="4fcf0-1983">Avbrotts förfrågan för värd klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="4fcf0-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="4fcf0-1985">**Ikonen** ![ Ikon för Pima-begäran i värd klass](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="4fcf0-1986">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1986">**Description**</span></span>

<span data-ttu-id="4fcf0-1987">Den här händelsen representerar en USBX värd klass Pima.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="4fcf0-1988">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1988">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1989">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-1990">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-1991">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-1992">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="4fcf0-1993">Pima-session för värd klass Stäng</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="4fcf0-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="4fcf0-1995">**Ikonen** ![ Pima för värd klassens stängnings ikon](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="4fcf0-1996">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1996">**Description**</span></span>

<span data-ttu-id="4fcf0-1997">Den här händelsen representerar en händelse för stängning av USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="4fcf0-1998">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1998">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-1999">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2000">Info-fält 2: Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="4fcf0-2001">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2002">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="4fcf0-2003">Pima-session för värd klass öppen</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="4fcf0-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="4fcf0-2005">**Ikonen** ![ Öppna Pima-ikonen för värd klassens session](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="4fcf0-2006">**Beskrivning** Den här händelsen representerar en USBX Pima session Open event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="4fcf0-2007">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2007">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2008">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2009">Info-fält 2: Pima-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="4fcf0-2010">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2011">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="4fcf0-2012">Pima lagrings-ID: n för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="4fcf0-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="4fcf0-2014">**Ikonen** ![ Pima lagrings-ID Hämta ikon för värd klass](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="4fcf0-2015">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2015">**Description**</span></span>

<span data-ttu-id="4fcf0-2016">Den här händelsen representerar en händelse för USBX-Pima för värd klass lagrings-ID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="4fcf0-2017">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2017">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2018">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2019">NFO-fält 2: matris för lagrings-ID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="4fcf0-2020">Informations fält 3: lagrings-ID-längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="4fcf0-2021">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="4fcf0-2022">Hämta lagrings information för värd klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="4fcf0-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="4fcf0-2024">**Ikonen** ![ Pima Storage information get-ikon i värd klass](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="4fcf0-2025">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2025">**Description**</span></span>

<span data-ttu-id="4fcf0-2026">Den här händelsen representerar en USBX värd klass Pima Storage information get event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="4fcf0-2027">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2027">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2028">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2029">Informations fält 2: lagrings-ID.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4fcf0-2030">Informations fält 3: lagring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="4fcf0-2031">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="4fcf0-2032">Pima-skjutreglage för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="4fcf0-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="4fcf0-2034">**Ikonen** ![ Ikon för Pima för värd klass](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="4fcf0-2035">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2035">**Description**</span></span>

<span data-ttu-id="4fcf0-2036">Den här händelsen representerar att ta emot en TCP-server-anslutning via nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="4fcf0-2037">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2037">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-2038">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2039">Info-fält 2: objekt referens.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4fcf0-2040">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2041">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="4fcf0-2042">Skrivning av värd klass Pima</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="4fcf0-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="4fcf0-2044">**Ikonen** ![ Pima Skriv ikon för värd klass](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="4fcf0-2045">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2045">**Description**</span></span>

<span data-ttu-id="4fcf0-2046">Den här händelsen representerar en USBX Pima skrivning av värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="4fcf0-2047">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2047">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2048">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-2049">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-2050">Informations fält 3: data längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="4fcf0-2051">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="4fcf0-2052">Aktivera värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="4fcf0-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="4fcf0-2054">**Ikonen** ![ Aktivera ikon för värd klass skrivare](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="4fcf0-2055">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2055">**Description**</span></span>

<span data-ttu-id="4fcf0-2056">Den här händelsen representerar en USBX-händelse för värd klass skrivare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="4fcf0-2057">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2057">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2058">Informations fält 1: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="4fcf0-2059">Info fält 2: pekare till Socket.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="4fcf0-2060">Informations fält 3: typ av tjänst.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="4fcf0-2061">Info fält 4: mottagnings fönster storlek.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="4fcf0-2062">Inaktivera värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="4fcf0-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="4fcf0-2064">**Ikonen** ![ Ikon för att inaktivera värd klass skrivare](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="4fcf0-2065">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2065">**Description**</span></span>

<span data-ttu-id="4fcf0-2066">Den här händelsen representerar en USBX-händelse för värd klass skrivare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-2067">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2067">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2068">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2069">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2070">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2071">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="4fcf0-2072">Hämta namn på värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="4fcf0-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="4fcf0-2074">**Ikonen** ![ Hämta ikon för värd klassens skrivar namn](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="4fcf0-2075">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2075">**Description**</span></span>

<span data-ttu-id="4fcf0-2076">Den här händelsen representerar en USBX-händelse för värd klass skrivare namn.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="4fcf0-2077">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2077">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-2078">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2079">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2080">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2081">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="4fcf0-2082">Läsning av värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="4fcf0-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="4fcf0-2084">**Ikonen** ![ Läs ikon för värd klass skrivare](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="4fcf0-2085">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2085">**Description**</span></span>

<span data-ttu-id="4fcf0-2086">Den här händelsen representerar en USBX-händelse för värd klass skrivare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="4fcf0-2087">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2087">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2088">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2089">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-2090">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-2091">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="4fcf0-2092">Mjuk återställning av värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="4fcf0-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="4fcf0-2094">**Ikonen** ![ Ikon för mjuk återställning av värd klass skrivare](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="4fcf0-2095">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2095">**Description**</span></span>

<span data-ttu-id="4fcf0-2096">Den här händelsen representerar en USBX-händelse för mjuk återställning av värd klass skrivare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="4fcf0-2097">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2097">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2098">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2099">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2100">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2101">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="4fcf0-2102">Hämta status för värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="4fcf0-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="4fcf0-2104">**Ikonen** ![ Ikon för Hämta värd klass skrivar status](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="4fcf0-2105">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2105">**Description**</span></span>

<span data-ttu-id="4fcf0-2106">Den här händelsen representerar en USBX-händelse för värd klass skrivare status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="4fcf0-2107">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2107">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2108">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2109">Info fält 2: skrivar status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="4fcf0-2110">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2111">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="4fcf0-2112">Skrivning av värd klass skrivare</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="4fcf0-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="4fcf0-2114">**Ikonen** ![ Skriv ikon för värd klass skrivare](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="4fcf0-2115">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2115">**Description**</span></span>

<span data-ttu-id="4fcf0-2116">Den här händelsen representerar en USBX skrivning av värd klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="4fcf0-2117">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2117">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-2118">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2119">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-2120">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-2121">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="4fcf0-2122">Aktivering av värd klass Prolific</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="4fcf0-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="4fcf0-2124">**Ikonen** ![ Prolific Aktivera ikon för värd klass](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="4fcf0-2125">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2125">**Description**</span></span>

<span data-ttu-id="4fcf0-2126">Den här händelsen representerar en USBX-Prolific aktiverings händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="4fcf0-2127">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2127">**Information Fields**</span></span> 

- <span data-ttu-id="4fcf0-2128">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2129">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2130">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2131">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="4fcf0-2132">Prolific inaktive ring av värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="4fcf0-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="4fcf0-2134">**Ikonen** ![ Prolific-ikon för värd klass](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="4fcf0-2135">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2135">**Description**</span></span>

<span data-ttu-id="4fcf0-2136">Den här händelsen representerar en USBX värd klass Prolific-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-2137">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2137">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2138">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2139">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2140">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2141">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="4fcf0-2142">Värd klass Prolific IOCTL Avbryt i pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="4fcf0-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="4fcf0-2144">**Ikonen** ![ Prolific för värd klass I O C T L Avbryt i pipe-ikon](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="4fcf0-2145">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2145">**Description**</span></span>

<span data-ttu-id="4fcf0-2146">Den här händelsen representerar en USBX för värd klass Prolific IOCTL abort i pipe-händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="4fcf0-2147">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2147">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2148">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2149">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2150">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2151">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="4fcf0-2152">Prolific för värd klass IOCTL avbryter pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="4fcf0-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="4fcf0-2154">**Ikonen** ![ Prolific för värd klass I O C T L ta bort pipe-ikon](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="4fcf0-2155">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2155">**Description**</span></span>

<span data-ttu-id="4fcf0-2156">Den här händelsen representerar en USBX för värd klass Prolific IOCTL-avbrott.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="4fcf0-2157">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2157">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2158">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2159">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2160">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2161">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="4fcf0-2162">Värd klass Prolific IOCTL Hämta enhets status</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="4fcf0-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="4fcf0-2164">**Ikonen** ![ Prolific för värd klass I O C T L, Hämta enhets status ikon](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="4fcf0-2165">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2165">**Description**</span></span>

<span data-ttu-id="4fcf0-2166">Den här händelsen representerar en USBX värd klass Prolific IOCTL get enhets status händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="4fcf0-2167">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2167">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2168">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2169">Info fält 2: enhets status.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="4fcf0-2170">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2171">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="4fcf0-2172">Prolific IOCTL get line-kodning i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="4fcf0-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="4fcf0-2174">**Ikonen** ![ Prolific för värd klass I O C T L, Hämta rad kodnings ikon](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="4fcf0-2175">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2175">**Description**</span></span>

<span data-ttu-id="4fcf0-2176">Den här händelsen representerar en USBX för värd klass Prolific IOCTL get line.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="4fcf0-2177">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2177">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2178">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2179">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-2180">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2181">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="4fcf0-2182">Prolific IOCTL-rensning för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="4fcf0-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="4fcf0-2184">**Ikonen** ![ Rensnings ikon för värd klassens Prolific IOCTL](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="4fcf0-2185">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2185">**Description**</span></span>

<span data-ttu-id="4fcf0-2186">Den här händelsen representerar en USBX för värd klass Prolific IOCTL.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="4fcf0-2187">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2187">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2188">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2189">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-2190">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2191">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="4fcf0-2192">Prolific IOCTL-rapport enhet för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="4fcf0-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="4fcf0-2194">**Ikonen** ![ Enhets ikon för värd klass Prolific I O d T L](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="4fcf0-2195">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2195">**Description**</span></span>

<span data-ttu-id="4fcf0-2196">Den här händelsen representerar en status ändrings händelse för en USBX Prolific IOCTL-rapport enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="4fcf0-2197">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2197">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2198">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2199">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-2200">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2201">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="4fcf0-2202">Prolific IOCTL för värd klass skicka rast</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="4fcf0-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="4fcf0-2204">**Ikonen** ![ Prolific för värd klass I O C T L](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="4fcf0-2205">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2205">**Description**</span></span>

<span data-ttu-id="4fcf0-2206">Den här händelsen representerar en USBX för värd klass Prolific IOCTL Send Break.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="4fcf0-2207">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2207">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2208">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2209">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2210">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2211">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="4fcf0-2212">Rad kodning för Prolific IOCTL för värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="4fcf0-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="4fcf0-2214">**Ikonen** ![ Prolific för värd klass I O C T L ange rad kodnings ikon](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="4fcf0-2215">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2215">**Description**</span></span>

<span data-ttu-id="4fcf0-2216">Den här händelsen representerar en USBX för värd klass Prolific IOCTL-uppsättning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="4fcf0-2217">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2217">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2218">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2219">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-2220">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2221">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="4fcf0-2222">Prolific IOCTL ange linje status i värd klass</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="4fcf0-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="4fcf0-2224">**Ikonen** ![ Ikon för värd klass Prolific I O C T L](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="4fcf0-2225">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2225">**Description**</span></span>

<span data-ttu-id="4fcf0-2226">Den här händelsen representerar en USBX värd klass Prolific IOCTL set line State event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="4fcf0-2227">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2227">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2228">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2229">Info fält 2: parameter.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4fcf0-2230">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2231">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="4fcf0-2232">Läsning av värd klass Prolific</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="4fcf0-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="4fcf0-2234">**Ikonen** ![ Läs ikon för värd klassen Prolific](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="4fcf0-2235">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2235">**Description**</span></span>

<span data-ttu-id="4fcf0-2236">Den här händelsen representerar en USBX värd klass Prolific Read event.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="4fcf0-2237">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2237">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2238">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2239">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-2240">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-2241">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="4fcf0-2242">Start av värd klass Prolific mottagning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="4fcf0-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="4fcf0-2244">**Ikonen** ![ Start ikon för Prolific mottagning i värd klass](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="4fcf0-2245">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2245">**Description**</span></span>

<span data-ttu-id="4fcf0-2246">Den här händelsen representerar start händelsen för en USBX värd klass Prolific.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="4fcf0-2247">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2247">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2248">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2249">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2250">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2251">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="4fcf0-2252">Sluta ta emot värd klass Prolific</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="4fcf0-2253">ux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="4fcf0-2254">**Ikonen** ![ Stopp ikon för Prolific för värd klass](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="4fcf0-2255">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2255">**Description**</span></span>

<span data-ttu-id="4fcf0-2256">Den här händelsen representerar en USBX för värd klass Prolific mottagning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="4fcf0-2257">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2257">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2258">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2259">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2260">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2261">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="4fcf0-2262">Skrivning av värd klass Prolific</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="4fcf0-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="4fcf0-2264">**Ikonen** ![ Prolific Skriv ikon för värd klass](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="4fcf0-2265">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2265">**Description**</span></span>

<span data-ttu-id="4fcf0-2266">Den här händelsen representerar en USBX Prolific Skriv händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="4fcf0-2267">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2267">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2268">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2269">Info fält 2: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4fcf0-2270">Informations fält 3: begärd längd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4fcf0-2271">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="4fcf0-2272">Aktivera värd klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="4fcf0-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="4fcf0-2274">**Ikonen** ![ Aktivera ikon för värd klass lagring](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="4fcf0-2275">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2275">**Description**</span></span>

<span data-ttu-id="4fcf0-2276">Den här händelsen representerar en händelse för aktivering av USBX värd klass lagring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="4fcf0-2277">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2277">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2278">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2279">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2280">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2281">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="4fcf0-2282">Inaktive ring av värd klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="4fcf0-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="4fcf0-2284">**Ikonen** ![ Ikon för värd klass lagrings inaktive ring](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="4fcf0-2285">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2285">**Description**</span></span>

<span data-ttu-id="4fcf0-2286">Den här händelsen representerar en USBX-händelse för värd klass lagring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="4fcf0-2287">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2287">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2288">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2289">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2290">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2291">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="4fcf0-2292">Hämtning av värd klassens lagrings medium kapacitet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="4fcf0-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="4fcf0-2294">**Ikonen** ![ Ikon för Hämta värd klass lagrings medie kapacitet](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="4fcf0-2295">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2295">**Description**</span></span>

<span data-ttu-id="4fcf0-2296">Den här händelsen representerar en händelse för USBX värd klass lagrings medie kapacitet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="4fcf0-2297">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2297">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2298">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2299">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2300">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2301">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="4fcf0-2302">Hämtnings kapacitet för värd klass lagrings medie format</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="4fcf0-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="4fcf0-2304">**Ikonen** ![ Ikon för Hämta kapacitet för värd klass lagrings medie format](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="4fcf0-2305">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2305">**Description**</span></span>

<span data-ttu-id="4fcf0-2306">Den här händelsen representerar en USBX-händelse för värd klass lagring med medie format.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="4fcf0-2307">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2307">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2308">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2309">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2310">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2311">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="4fcf0-2312">Montering av värd klass lagrings medium</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="4fcf0-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="4fcf0-2314">**Ikonen** ![ Monterings ikon för värd klass lagrings medium](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="4fcf0-2315">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2315">**Description**</span></span>

<span data-ttu-id="4fcf0-2316">Den här händelsen representerar en USBX för värd klass lagrings medier.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="4fcf0-2317">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2317">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2318">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2319">Info fält 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4fcf0-2320">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2321">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="4fcf0-2322">Lagrings medier för värd klass öppen</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="4fcf0-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="4fcf0-2324">**Ikonen** ![ Öppnings ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="4fcf0-2325">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2325">**Description**</span></span>

<span data-ttu-id="4fcf0-2326">Den här händelsen representerar en USBX-händelse för värd klass lagrings medier.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="4fcf0-2327">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2327">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2328">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2329">Info fält 2: medium.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="4fcf0-2330">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2331">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="4fcf0-2332">Läsning av värd klassens lagrings medium</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="4fcf0-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="4fcf0-2334">**Ikonen** ![ Läs ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="4fcf0-2335">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2335">**Description**</span></span>

<span data-ttu-id="4fcf0-2336">Den här händelsen representerar en USBX för värd klass lagrings medier.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="4fcf0-2337">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2337">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2338">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2339">Info fält 2: sektor start.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="4fcf0-2340">Informations fält 3: antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="4fcf0-2341">Info-fält 4: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="4fcf0-2342">Skrivning av värd klass lagrings medium</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="4fcf0-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="4fcf0-2344">**Ikonen** ![ Skriv ikon för värd klassens lagrings medium](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="4fcf0-2345">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2345">**Description**</span></span>

<span data-ttu-id="4fcf0-2346">Den här händelsen representerar en Skriv händelse för USBX Host Class Storage media.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="4fcf0-2347">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2347">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2348">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2349">Info fält 2: sektor start.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="4fcf0-2350">Informations fält 3: antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="4fcf0-2351">Info-fält 4: data pekare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="4fcf0-2352">Sense-begäran om värd klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="4fcf0-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="4fcf0-2354">**Ikonen** ![ Ikon för värd klass lagrings förfrågan Sense](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="4fcf0-2355">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2355">**Description**</span></span>

<span data-ttu-id="4fcf0-2356">Den här händelsen representerar en USBX-händelse för värd klass lagrings begär Anden.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="4fcf0-2357">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2357">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2358">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2359">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2360">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2361">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="4fcf0-2362">Start stopp för värd klass lagring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="4fcf0-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="4fcf0-2364">**Ikonen** ![ Start stopp ikon för värd klass lagring](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="4fcf0-2365">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2365">**Description**</span></span>

<span data-ttu-id="4fcf0-2366">Den här händelsen representerar en USBX för värd klass lagrings start.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="4fcf0-2367">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2367">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2368">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2369">Informations fält 2: starta stopp signal.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="4fcf0-2370">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2371">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="4fcf0-2372">Redo test för värd klass lagrings enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="4fcf0-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="4fcf0-2374">**Ikonen** ![ Test ikon för värd klassens lagrings enhet](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="4fcf0-2375">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2375">**Description**</span></span>

<span data-ttu-id="4fcf0-2376">Den här händelsen representerar test händelsen för USBX värd klass lagrings enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="4fcf0-2377">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2377">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2378">Informations fält 1: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4fcf0-2379">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2380">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2381">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="4fcf0-2382">Värd Stack klass instans skapa</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="4fcf0-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="4fcf0-2384">**Ikonen** ![ Ikon för att skapa värd Stack klass instans](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="4fcf0-2385">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2385">**Description**</span></span>

<span data-ttu-id="4fcf0-2386">Den här händelsen representerar en händelse för att skapa en USBX Host stack-instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="4fcf0-2387">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2387">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2388">Informations fält 1: klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="4fcf0-2389">Informations fält 2: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-2390">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2391">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="4fcf0-2392">Förstöra värd Stack klass instans</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="4fcf0-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="4fcf0-2394">**Ikonen** ![ Ikon för att förstöra värd Stack klass instans](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="4fcf0-2395">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2395">**Description**</span></span>

<span data-ttu-id="4fcf0-2396">Den här händelsen representerar en händelse för förstöring av USBX Host stack-instanser.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="4fcf0-2397">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2397">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2398">Informations fält 1: klass.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="4fcf0-2399">Informations fält 2: klass instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="4fcf0-2400">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2401">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="4fcf0-2402">Ta bort värd stack konfiguration</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="4fcf0-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="4fcf0-2404">**Ikonen** ![ Borttagnings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="4fcf0-2405">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2405">**Description**</span></span>

<span data-ttu-id="4fcf0-2406">Den här händelsen representerar en händelse för borttagning av en USBX Host stack-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="4fcf0-2407">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2407">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2408">Informations fält 1: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2409">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2410">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2411">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="4fcf0-2412">Uppräkning av värd stack konfiguration</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="4fcf0-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="4fcf0-2414">**Ikonen** ![ Uppräknings ikon för värd stack konfiguration](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="4fcf0-2415">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2415">**Description**</span></span>

<span data-ttu-id="4fcf0-2416">Den här händelsen representerar en uppräknings händelse för USBX Host stack-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="4fcf0-2417">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2417">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2418">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2419">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2420">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2421">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="4fcf0-2422">Skapa stack konfigurations instans</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="4fcf0-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="4fcf0-2424">**Ikonen** ![ Skapa ikon för stack konfigurations instans](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="4fcf0-2425">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2425">**Description**</span></span>

<span data-ttu-id="4fcf0-2426">Den här händelsen representerar en USBX för att skapa en händelse i värd stacken.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="4fcf0-2427">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2427">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2428">Informations fält 1: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2429">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2430">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2431">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="4fcf0-2432">Borttagning av värd Stacks konfigurations instans</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="4fcf0-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="4fcf0-2434">**Ikonen** ![ Borttagnings ikon för värd Stacks konfigurations instans](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="4fcf0-2435">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2435">**Description**</span></span>

<span data-ttu-id="4fcf0-2436">Den här händelsen representerar en USBX-händelse som tar bort värd Stacks konfigurations instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="4fcf0-2437">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2437">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2438">Informations fält 1: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2439">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2440">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2441">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="4fcf0-2442">Konfigurations uppsättning för värd stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="4fcf0-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="4fcf0-2444">**Ikonen** ![ Ikon för konfigurations uppsättning för värd stack](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="4fcf0-2445">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2445">**Description**</span></span>

<span data-ttu-id="4fcf0-2446">Den här händelsen representerar en händelse för konfigurations uppsättning för USBX värd stack.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="4fcf0-2447">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2447">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2448">Informations fält 1: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2449">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2450">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2451">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="4fcf0-2452">Adress uppsättning för värd stack enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="4fcf0-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="4fcf0-2454">**Ikonen** ![ Ikon för värd stack enhetens adress uppsättning](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="4fcf0-2455">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2455">**Description**</span></span>

<span data-ttu-id="4fcf0-2456">Den här händelsen representerar en händelse för en USBX-värd för stack enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="4fcf0-2457">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2457">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2458">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2459">Info fält 2: enhets adress.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="4fcf0-2460">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2461">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="4fcf0-2462">Hämta konfiguration av värd stack enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="4fcf0-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="4fcf0-2464">**Ikonen** ![ Hämta ikon för värd stack enhets konfiguration](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="4fcf0-2465">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2465">**Description**</span></span>

<span data-ttu-id="4fcf0-2466">Den här händelsen representerar en USBX värd stack enhets konfiguration Hämta händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="4fcf0-2467">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2467">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2468">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2469">NFO-fält 2: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2470">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2471">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="4fcf0-2472">Välj konfiguration av värd stack enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="4fcf0-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="4fcf0-2474">**Ikonen** ![ Konfiguration av värd stack enhets konfiguration Välj ikon](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="4fcf0-2475">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2475">**Description**</span></span>

<span data-ttu-id="4fcf0-2476">Den här händelsen representerar en USBX för värd stack enhets konfiguration Välj händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="4fcf0-2477">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2477">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2478">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2479">Info fält 2: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2480">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2481">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="4fcf0-2482">Läsning av värd stack enhets Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="4fcf0-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="4fcf0-2484">**Ikonen** ![ Läs ikon för värd stack enhets Beskrivning](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="4fcf0-2485">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2485">**Description**</span></span>

<span data-ttu-id="4fcf0-2486">Den här händelsen representerar läsnings händelsen för en USBX värd Stacks enhets beskrivning.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="4fcf0-2487">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2487">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2488">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2489">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2490">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2491">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="4fcf0-2492">Hämta värd stack enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="4fcf0-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="4fcf0-2494">**Ikonen** ![ Hämta ikon för värd stack enhet](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="4fcf0-2495">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2495">**Description**</span></span>

<span data-ttu-id="4fcf0-2496">Den här händelsen representerar en händelse för att hämta en USBX värd stack enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="4fcf0-2497">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2497">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2498">Informations fält 1: enhets index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="4fcf0-2499">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2500">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2501">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="4fcf0-2502">Ta bort värd stack enhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="4fcf0-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="4fcf0-2504">**Ikonen** ![ Ikon för att ta bort värd stack enhet](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="4fcf0-2505">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2505">**Description**</span></span>

<span data-ttu-id="4fcf0-2506">Den här händelsen representerar en händelse för att ta bort en USBX Host stack-enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="4fcf0-2507">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2507">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2508">Info-fält 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4fcf0-2509">Info-fält 2: överordnad.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="4fcf0-2510">Info-fält 3: port index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="4fcf0-2511">Info fält 4: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="4fcf0-2512">Värd stack för enhets resurs kostnads fritt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="4fcf0-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="4fcf0-2514">**Ikonen** ![ Ikon för värd stack för enhets resurs](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="4fcf0-2515">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2515">**Description**</span></span>

<span data-ttu-id="4fcf0-2516">Den här händelsen representerar en ledig händelse för en USBX värd stack för enhets resurser.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="4fcf0-2517">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2517">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2518">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2519">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2520">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2521">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="4fcf0-2522">Skapa värd stack slut punkts instans skapa</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="4fcf0-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="4fcf0-2524">**Ikonen** ![ Ikon för att skapa värd stack slut punkts instans](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="4fcf0-2525">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2525">**Description**</span></span>

<span data-ttu-id="4fcf0-2526">Den här händelsen representerar en händelse för att skapa en USBX Host stack-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="4fcf0-2527">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2527">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2528">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2529">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2530">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2531">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="4fcf0-2532">Ta bort värd stack slut punkts instans</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="4fcf0-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="4fcf0-2534">**Ikonen** ![ Borttagnings ikon för värd stack slut punkts instans](./media/user-guide/usbx-events/image200.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="4fcf0-2535">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2535">**Description**</span></span>

<span data-ttu-id="4fcf0-2536">Den här händelsen representerar en händelse för borttagning av en USBX Host stack-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="4fcf0-2537">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2537">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2538">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2539">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2540">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="4fcf0-2541">Återställning av värd stack slut punkt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="4fcf0-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="4fcf0-2543">**Ikonen** ![ Ikon för återställning av värd stack slut punkt](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="4fcf0-2544">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2544">**Description**</span></span>

<span data-ttu-id="4fcf0-2545">Den här händelsen representerar en händelse för återställning av USBX värd stack slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="4fcf0-2546">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2546">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2547">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2548">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2549">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2550">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="4fcf0-2551">Avbrytning av värd stack slut punkts överföring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="4fcf0-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="4fcf0-2553">**Ikonen** ![ Avbryt ikon för värd stack slut punkts överföring](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="4fcf0-2554">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2554">**Description**</span></span>

<span data-ttu-id="4fcf0-2555">Den här händelsen representerar en avbrotts händelse för USBX värd stack slut punkts överföring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="4fcf0-2556">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2556">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2557">Informations fält 1: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2558">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2559">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2560">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="4fcf0-2561">Värd styrenhet registrera värd styrenhet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="4fcf0-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="4fcf0-2563">**Ikonen** ![ Registrerings ikon för värd stack värd styrenhet](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="4fcf0-2564">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2564">**Description**</span></span>

<span data-ttu-id="4fcf0-2565">Den här händelsen representerar en register värd styrenhet för USBX värd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="4fcf0-2566">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2566">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2567">Info-fält 1: HCD-namn.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="4fcf0-2568">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2569">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2570">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="4fcf0-2571">Värd stack initieras</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="4fcf0-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="4fcf0-2573">**Ikonen** ![ Ikon för att initiera värd stack](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="4fcf0-2574">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2574">**Description**</span></span>

<span data-ttu-id="4fcf0-2575">Den här händelsen representerar en händelse för att initiera en USBX-värd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="4fcf0-2576">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2576">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2577">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4fcf0-2578">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2579">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2580">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="4fcf0-2581">Hämtning av värd stack gränssnitt slut punkt</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="4fcf0-2582">Interface_ TCP-återförsöksintervallet</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="4fcf0-2583">**Ikonen** ![ Hämta ikon för värd stackens gränssnitts slut punkt](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="4fcf0-2584">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2584">**Description**</span></span>

<span data-ttu-id="4fcf0-2585">Den här händelsen representerar en intern NetX-händelse för TCP-försök.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="4fcf0-2586">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2586">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2587">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-2588">Info-fält 2: slut punkts index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="4fcf0-2589">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2590">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="4fcf0-2591">Skapa värd stack gränssnitts instans</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="4fcf0-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="4fcf0-2593">**Ikonen** ![ Ikon för att skapa värd stack gränssnitts instans](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="4fcf0-2594">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2594">**Description**</span></span>

<span data-ttu-id="4fcf0-2595">Den här händelsen representerar en USBX-händelse för en värd stack instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="4fcf0-2596">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2596">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2597">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-2598">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2599">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2600">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="4fcf0-2601">Borttagning av värd Stacks gränssnitts instans</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="4fcf0-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="4fcf0-2603">**Ikonen** ![ Borttagnings ikon för värd stackens gränssnitts instans](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="4fcf0-2604">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2604">**Description**</span></span>

<span data-ttu-id="4fcf0-2605">Den här händelsen representerar en händelse för borttagning av en USBX Host stack Interface-instans.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="4fcf0-2606">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2606">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2607">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-2608">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2609">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2610">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="4fcf0-2611">Värd stack gränssnitts uppsättning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="4fcf0-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="4fcf0-2613">**Ikonen** ![ Ikon för värd stack gränssnitts uppsättning](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="4fcf0-2614">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2614">**Description**</span></span>

<span data-ttu-id="4fcf0-2615">Den här händelsen representerar en händelse för en gränssnitts uppsättning för USBX värd stack.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="4fcf0-2616">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2616">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2617">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-2618">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2619">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2620">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="4fcf0-2621">Inställning av värd stack gränssnitt Välj</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="4fcf0-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="4fcf0-2623">**Ikonen** ![ Inställnings ikon för värd Stacks gränssnitt](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="4fcf0-2624">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2624">**Description**</span></span>

<span data-ttu-id="4fcf0-2625">Den här händelsen representerar en gränssnitts inställning för en USBX. Välj händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="4fcf0-2626">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2626">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2627">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-2628">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2629">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2630">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="4fcf0-2631">Värd stack ny konfiguration skapa</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="4fcf0-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="4fcf0-2633">**Ikonen** ![ Värd stack ny ikon för att skapa konfiguration](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="4fcf0-2634">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2634">**Description**</span></span>
 
<span data-ttu-id="4fcf0-2635">Den här händelsen representerar en ny konfiguration för att skapa en USBX-värd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="4fcf0-2636">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2636">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2637">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2638">Info fält 2: konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="4fcf0-2639">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2640">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="4fcf0-2641">Skapa värd stack ny enhet skapa</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="4fcf0-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="4fcf0-2643">**Ikonen** ![ Ikon för att skapa en ny enhet för värd stack](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="4fcf0-2644">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2644">**Description**</span></span>
 
 <span data-ttu-id="4fcf0-2645">Den här händelsen representerar en USBX-värd stack ny enhet skapa händelse.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="4fcf0-2646">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2646">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2647">Info-fält 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4fcf0-2648">Informations fält 2: enhets ägare.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="4fcf0-2649">Info-fält 3: port index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="4fcf0-2650">Info fält 4: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="4fcf0-2651">Skapa en ny slut punkt för värd stack</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="4fcf0-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="4fcf0-2653">**Ikonen** ![ Skapa ikon för värd stack för ny slut punkt](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="4fcf0-2654">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2654">**Description**</span></span>
 
<span data-ttu-id="4fcf0-2655">Den här händelsen representerar en ny slut punkt för att skapa en USBX-värd.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="4fcf0-2656">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2656">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2657">Informations fält 1: gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4fcf0-2658">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2659">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2660">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="4fcf0-2661">Ändrings process för stacken för värd stackens rot nav</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="4fcf0-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="4fcf0-2663">**Ikonen** ![ Ikon för ändrings process för värd stackens rot nav](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="4fcf0-2664">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2664">**Description**</span></span>
 
<span data-ttu-id="4fcf0-2665">Den här händelsen representerar en ändrings process för USBX värd stackens rot nav.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="4fcf0-2666">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2666">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2667">Info fält 1: port index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="4fcf0-2668">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4fcf0-2669">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2670">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="4fcf0-2671">Värd stack för rot nav enhets extrahering</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="4fcf0-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="4fcf0-2673">**Ikonen** ![ Ikon för extrahering av värd stack för rot nav](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="4fcf0-2674">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2674">**Description**</span></span>

<span data-ttu-id="4fcf0-2675">Den här händelsen representerar en USBX värd stack för enhets stacken.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="4fcf0-2676">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2676">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2677">Info-fält 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4fcf0-2678">Info fält 2: port index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="4fcf0-2679">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2680">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="4fcf0-2681">Värd stack för rot Hubbs enhets infogning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="4fcf0-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="4fcf0-2683">**Ikonen** ![ Ikon för värd stack för rot nav enhet](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="4fcf0-2684">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2684">**Description**</span></span>

<span data-ttu-id="4fcf0-2685">Den här händelsen representerar en USBX som anger att enheten ska infogas i värd stacken.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="4fcf0-2686">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2686">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2687">Info-fält 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4fcf0-2688">Info fält 2: port index.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="4fcf0-2689">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2690">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="4fcf0-2691">Begäran om värd stack överföring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="4fcf0-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="4fcf0-2693">**Ikonen** ![ Ikon för värd stack överförings förfrågan](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="4fcf0-2694">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2694">**Description**</span></span>

<span data-ttu-id="4fcf0-2695">Den här händelsen representerar en begäran om USBX värd stack överföring.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="4fcf0-2696">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2696">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2697">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2698">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2699">Info fält 3: överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="4fcf0-2700">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="4fcf0-2701">Avbryt begäran om värd stack överföring</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="4fcf0-2702">Status för intern I/O-drivrutin för hämtning</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="4fcf0-2703">**Ikonen** ![ Avbryt ikon för begäran om värd stack överföring](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="4fcf0-2704">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2704">**Description**</span></span>

<span data-ttu-id="4fcf0-2705">Den här händelsen representerar en begäran om att USBX värd stack överföring avbryts.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="4fcf0-2706">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2706">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2707">Info fält 1: enhet.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="4fcf0-2708">Info fält 2: slut punkt.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4fcf0-2709">Info fält 3: överförings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="4fcf0-2710">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="4fcf0-2711">USBX-fel</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="4fcf0-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2712">ux_error</span></span>

<span data-ttu-id="4fcf0-2713">**Ikonen** ![ Fel ikon för U S B X](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="4fcf0-2714">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2714">**Description**</span></span>

<span data-ttu-id="4fcf0-2715">Den här händelsen representerar en fel händelse för USBX.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="4fcf0-2716">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2716">**Information Fields**</span></span>

- <span data-ttu-id="4fcf0-2717">Informations fält 1: USBX-fel.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="4fcf0-2718">Informations fält 2: fel namn.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="4fcf0-2719">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4fcf0-2720">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="4fcf0-2720">Info Field 4: Not used.</span></span>