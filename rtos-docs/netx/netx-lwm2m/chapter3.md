---
title: Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-LWM2M
description: Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX-LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826679"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="a5143-103">Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-LWM2M</span><span class="sxs-lookup"><span data-stu-id="a5143-103">Chapter 3 - Functional description of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="a5143-104">Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX-LWM2M.</span><span class="sxs-lookup"><span data-stu-id="a5143-104">This chapter contains a functional description of Azure RTOS NetX LWM2M.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="a5143-105">LWM2M klient initiering</span><span class="sxs-lookup"><span data-stu-id="a5143-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="a5143-106">LWM2M-klienten initieras genom att anropa ***nx_lwm2m_client_creates*** tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a5143-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="a5143-107">LWM2M-klienten körs i sin egen tråd och kan rapportera vissa händelser till programmet genom att använda återanrop eller genom att anropa metoder för de anpassade objekt som implementeras av programmet.</span><span class="sxs-lookup"><span data-stu-id="a5143-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="a5143-108">Dessutom måste LWM2M-klientsessioner skapas genom att anropa ***nx_lwm2m_client_session_create*** för att aktivera kommunikation med en eller flera servrar.</span><span class="sxs-lookup"><span data-stu-id="a5143-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="a5143-109">En session kan kommunicera med två olika typer av servrar: en Start Server eller en LWM2M-Server (enhets hantering).</span><span class="sxs-lookup"><span data-stu-id="a5143-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="a5143-110">Bootstrap-Server-session</span><span class="sxs-lookup"><span data-stu-id="a5143-110">Bootstrap Server Session</span></span>

<span data-ttu-id="a5143-111">En kommunikations-session med en Start Server används för att tillhandahålla viktig information till LWM2M-klienten så att LWM2M-klienten kan utföra åtgärden "Registrera" med en eller flera LWM2M-servrar.</span><span class="sxs-lookup"><span data-stu-id="a5143-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation "Register" with one or more LWM2M Servers.</span></span> <span data-ttu-id="a5143-112">Den här typen av Server används vid start läge för klienten som initierats och initierats av servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="a5143-113">Programmet kan starta en bootstrap-session genom att anropa ***nx_lwm2m_client_session_bootstrap** _ eller _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, den måste ange IP-adressen och port numret för-servern och ett valfritt säkerhets objekts instans-ID.</span><span class="sxs-lookup"><span data-stu-id="a5143-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="a5143-114">Funktionen _*_nx_lwm2m_client_session_bootstrap_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* upprättar en säker DTLS-anslutning till servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="a5143-115">Om bootstrap-åtgärden lyckas ska start servern ha skapat säkerhets objekts instanser för start-och LWM2M-servrarna och Server objekt instanser för LWM2M-servrarna.</span><span class="sxs-lookup"><span data-stu-id="a5143-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="a5143-116">Programmet måste använda den här informationen för att upprätta en session med LWM2M-servrar.</span><span class="sxs-lookup"><span data-stu-id="a5143-116">The application must use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="a5143-117">Bootstrap-data ska sparas till beständigt minne av programmet för att konfigurera LWM2M-klienten vid nästa omstart av enheten.</span><span class="sxs-lookup"><span data-stu-id="a5143-117">The Bootstrap data should be saved to non-volatile memory by the application in order to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="a5143-118">LWM2M Server-session</span><span class="sxs-lookup"><span data-stu-id="a5143-118">LWM2M Server Session</span></span>

<span data-ttu-id="a5143-119">En kommunikations-session med en LWM2M-Server används för registrering, enhets hantering och tjänst aktivering.</span><span class="sxs-lookup"><span data-stu-id="a5143-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="a5143-120">Programmet kan registrera LWM2M-klienten på en server genom att anropa ***nx_lwm2m_client_session_register** _ eller _*_nx_lwm2m_client_session_register_dtls_\*_, den måste ange IP-adressen och port numret för-servern och det korta Server-ID som motsvarar en befintlig server objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="a5143-121">Funktionen _*_nx_lwm2m_client_session_register_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_register_dtls_*\* upprättar en säker DTLS-anslutning till servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="a5143-122">Programmet kan avregistrera LWM2M-klienten genom att anropa \***nx_lwm2m_client_session_deregister** _ och be klienten att skicka ett uppdaterings meddelande genom att anropa _ *_nx_lwm2m_client_session_update_* \*.</span><span class="sxs-lookup"><span data-stu-id="a5143-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an 'Update' message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="a5143-123">Motanrop för sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="a5143-123">Session State Callback</span></span>

<span data-ttu-id="a5143-124">Programmet registrerar ett återanrop vid skapandet av en session som anropas när sessionens tillstånd uppdateras, motringningsfunktionen NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK har följande prototyp:</span><span class="sxs-lookup"><span data-stu-id="a5143-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK has the following prototype:</span></span>

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

<span data-ttu-id="a5143-125">Följande tillstånd definieras:</span><span class="sxs-lookup"><span data-stu-id="a5143-125">The following states are defined :</span></span>

- <span data-ttu-id="a5143-126">**NX_LWM2M_CLIENT_SESSION_INIT**: initialt tillstånd efter att sessionen skapats.</span><span class="sxs-lookup"><span data-stu-id="a5143-126">**NX_LWM2M_CLIENT_SESSION_INIT**: The initial state after session creation.</span></span>

- <span data-ttu-id="a5143-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: klienten väntar på att den väntande vänte tiden eller servern har initierats.</span><span class="sxs-lookup"><span data-stu-id="a5143-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: The client is waiting for the expiration of the 'Hold Off' timer or Server Initiated Bootstrap.</span></span>

- <span data-ttu-id="a5143-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: klienten har skickat ett "Request"-meddelande till bootstrap-servern (klienten initierade start).</span><span class="sxs-lookup"><span data-stu-id="a5143-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: The client has sent a 'Request' message to the Bootstrap Server (Client Initiated Bootstrap).</span></span>

- <span data-ttu-id="a5143-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: klienten tar emot data från start servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: The client is receiving data from the Bootstrap Server.</span></span>

- <span data-ttu-id="a5143-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: bootstrap-servern har skickat ett meddelande om att det har skickats.</span><span class="sxs-lookup"><span data-stu-id="a5143-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: The Bootstrap Server has sent a 'Finished' message.</span></span>

- <span data-ttu-id="a5143-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: bootstrap-sessionen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="a5143-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: The bootstrap session has failed.</span></span>

- <span data-ttu-id="a5143-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: klienten har skickat ett "Registrera"-meddelande till LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: The client has sent a 'Register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="a5143-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: klienten är registrerad på LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: The client is registered to the LWM2M Server.</span></span>

- <span data-ttu-id="a5143-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: klienten har skickat ett uppdaterings meddelande till LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: The client has sent an 'Update' message to the LWM2M Server.</span></span>

- <span data-ttu-id="a5143-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: klienten har skickat meddelandet "avregistrera" till LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: The client has sent an 'De-register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="a5143-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: klienten AVREGISTRERAS från LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: The client is de-registered from the LWM2M Server.</span></span>

- <span data-ttu-id="a5143-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: LWM2M-servern är inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="a5143-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: The LWM2M Server is disabled.</span></span> <span data-ttu-id="a5143-138">En "Registrera" skickas när den inaktiverade timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="a5143-138">A 'Register' will be sent after the expiration of the disable timer.</span></span>

- <span data-ttu-id="a5143-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: det gick inte att utföra registreringen eller uppdateringen på LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="a5143-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: The registration or update operation to the LWM2M Server has failed.</span></span>

- <span data-ttu-id="a5143-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: den server objekt instans som motsvarar LWM2M-servern har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="a5143-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> <span data-ttu-id="a5143-141">Om ett fel uppstår kan programmet Hämta orsaken till felet genom att anropa **_nx_lwm2m_client_session_error_get_**.</span><span class="sxs-lookup"><span data-stu-id="a5143-141">In case of error the application can retrieve the cause of the error by calling **_nx_lwm2m_client_session_error_get_**.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="a5143-142">Hantering av lokala enheter</span><span class="sxs-lookup"><span data-stu-id="a5143-142">Local Device Management</span></span>

<span data-ttu-id="a5143-143">Programmet kan komma åt objekten i LWM2M-klienten med hjälp av funktionerna för lokal enhets hantering.</span><span class="sxs-lookup"><span data-stu-id="a5143-143">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="a5143-144">Följande funktioner är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="a5143-144">The following functions are provided:</span></span>

- <span data-ttu-id="a5143-145">***nx_lwm2m_client_object_read***: läsa resurser från en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-145">***nx_lwm2m_client_object_read***: Read resources from an Object Instance.</span></span>

- <span data-ttu-id="a5143-146">***nx_lwm2m_client_object_discover***: Hämta en lista över resurser för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-146">***nx_lwm2m_client_object_discover***: Get the list of the resources of an Object Instance.</span></span>

- <span data-ttu-id="a5143-147">***nx_lwm2m_client_object_write***: skriva resurser till en objekt instans</span><span class="sxs-lookup"><span data-stu-id="a5143-147">***nx_lwm2m_client_object_write***: Write resources to an Object Instance</span></span>

- <span data-ttu-id="a5143-148">***nx_lwm2m_client_object_execute***: utför åtgärden kör på en resurs av en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-148">***nx_lwm2m_client_object_execute***: Perform the Execute operation on a resource of an Object Instance.</span></span>

- <span data-ttu-id="a5143-149">***nx_lwm2m_client_object_create***: skapa en ny objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-149">***nx_lwm2m_client_object_create***: Create a new Object Instance.</span></span>

- <span data-ttu-id="a5143-150">***nx_lwm2m_client_object_delete***: ta bort en befintlig objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-150">***nx_lwm2m_client_object_delete***: Delete an existing Object Instance.</span></span>

- <span data-ttu-id="a5143-151">***nx_lwm2m_client_object_get_next***: Hämta nästa objekt-ID som implementeras av Lwm2m-klienten.</span><span class="sxs-lookup"><span data-stu-id="a5143-151">***nx_lwm2m_client_object_get_next***: Get the next Object ID implemented by the LWM2M Client.</span></span>

- <span data-ttu-id="a5143-152">***nx_lwm2m_client_object_instance_get_next***: Hämta nästa instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a5143-152">***nx_lwm2m_client_object_instance_get_next***: Get the next Instance of an Object.</span></span>

## <a name="resource-information"></a><span data-ttu-id="a5143-153">Resursinformation</span><span class="sxs-lookup"><span data-stu-id="a5143-153">Resource Information</span></span>

<span data-ttu-id="a5143-154">Vid läsning från och skrivning till objekt representeras en resurs av NX_LWM2M_RESOURCE-strukturen.</span><span class="sxs-lookup"><span data-stu-id="a5143-154">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="a5143-155">Den här strukturen innehåller ID: t för resursen/instansen och dess värde.</span><span class="sxs-lookup"><span data-stu-id="a5143-155">This structure contains the ID of the Resource/Instance and its value.</span></span> <span data-ttu-id="a5143-156">Kodningen för värdet beror på dess typ och ursprung (program eller nätverk).</span><span class="sxs-lookup"><span data-stu-id="a5143-156">The encoding of the value depends on its type and its origin (application or network).</span></span>

<span data-ttu-id="a5143-157">NX_LWM2M_RESOURCEs strukturen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-157">The NX_LWM2M_RESOURCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- <span data-ttu-id="a5143-158">**nx_lwm2m_resource_id**: ID för resursen eller instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-158">**nx_lwm2m_resource_id**: The ID of the Resource or the Instance.</span></span>
- <span data-ttu-id="a5143-159">**nx_lwm2m_resource_type**: värdets typ, se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-159">**nx_lwm2m_resource_type**: The type of the value, see below.</span></span>
- <span data-ttu-id="a5143-160">**nx_lwm2m_resource_value**: resursens värde beror på typen av värde.</span><span class="sxs-lookup"><span data-stu-id="a5143-160">**nx_lwm2m_resource_value**: The value of the Resource, depends on the type of the value.</span></span>

<span data-ttu-id="a5143-161">Följande typ av värden definieras:</span><span class="sxs-lookup"><span data-stu-id="a5143-161">The following type of values are defined :</span></span>

- <span data-ttu-id="a5143-162">**NX_LWM2M_RESOURCE_NONE**: Tom resurs.</span><span class="sxs-lookup"><span data-stu-id="a5143-162">**NX_LWM2M_RESOURCE_NONE**: Empty resource.</span></span>

- <span data-ttu-id="a5143-163">**NX_LWM2M_RESOURCE_STRING**: ett null-avslutat UTF-8-sträng värde lagrat i *nx_lwm2m_resource_stringdata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-163">**NX_LWM2M_RESOURCE_STRING**: A null-terminated UTF-8 string value stored in *nx_lwm2m_resource_stringdata*.</span></span>

- <span data-ttu-id="a5143-164">**NX_LWM2M_RESOURCE_INTEGER32**: ett 32-bitars heltals värde lagrat i *nx_lwm2m_resource_integer32data*.</span><span class="sxs-lookup"><span data-stu-id="a5143-164">**NX_LWM2M_RESOURCE_INTEGER32**: A 32-Bit Integer value stored in *nx_lwm2m_resource_integer32data*.</span></span>

- <span data-ttu-id="a5143-165">**NX_LWM2M_RESOURCE_INTEGER64**: ett 64-bitars heltals värde lagrat i *nx_lwm2m_resource_integer64data*.</span><span class="sxs-lookup"><span data-stu-id="a5143-165">**NX_LWM2M_RESOURCE_INTEGER64**: A 64-Bit Integer value stored in *nx_lwm2m_resource_integer64data*.</span></span>

- <span data-ttu-id="a5143-166">**NX_LWM2M_RESOURCE_FLOAT32**: ett 32-bitars flytt ALS värde som lagras i *nx_lwm2m_resource_float32data*.</span><span class="sxs-lookup"><span data-stu-id="a5143-166">**NX_LWM2M_RESOURCE_FLOAT32**: A 32-Bit Floating Point value stored in *nx_lwm2m_resource_float32data*.</span></span>

- <span data-ttu-id="a5143-167">**NX_LWM2M_RESOURCE_FLOAT64**: ett 64-bitars flytt ALS värde som lagras i *nx_lwm2m_resource_float64data*.</span><span class="sxs-lookup"><span data-stu-id="a5143-167">**NX_LWM2M_RESOURCE_FLOAT64**: A 64-Bit Floating Point value stored in *nx_lwm2m_resource_float64data*.</span></span>

- <span data-ttu-id="a5143-168">**NX_LWM2M_RESOURCE_BOOLEAN**: ett booleskt värde lagrat i *nx_lwm2m_resource_booleandata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-168">**NX_LWM2M_RESOURCE_BOOLEAN**: A Boolean value stored in *nx_lwm2m_resource_booleandata*.</span></span>

- <span data-ttu-id="a5143-169">**NX_LWM2M_RESOURCE_OPAQUE**: ett ogenomskinligt värde som definieras av *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-169">**NX_LWM2M_RESOURCE_OPAQUE**: An Opaque value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="a5143-170">**NX_LWM2M_RESOURCE_OBJLNK**: ett objekt länk värde lagrat i *nx_lwm2m_resource_objlnkdata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-170">**NX_LWM2M_RESOURCE_OBJLNK**: An Object Link value stored in *nx_lwm2m_resource_objlnkdata*.</span></span>

- <span data-ttu-id="a5143-171">**NX_LWM2M_RESOURCE_TLV**: ett TLV-kodat värde som definieras av *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-171">**NX_LWM2M_RESOURCE_TLV**: A TLV encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="a5143-172">**NX_LWM2M_RESOURCE_TEXT**: ett Plain-Text-kodat värde som definieras av *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-172">**NX_LWM2M_RESOURCE_TEXT**: A Plain-Text encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="a5143-173">**NX_LWM2M_RESOURCE_MULTIPLE**: en flera resurs som definieras av *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-173">**NX_LWM2M_RESOURCE_MULTIPLE**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="a5143-174">*nx_lwm2m_resource_multiple_ptr* är en pekare till en matris med **NX_LWM2M_RESOURCE** strukturer som innehåller information om varje resurs instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-174">*nx_lwm2m_resource_multiple_ptr* is a pointer to an array of **NX_LWM2M_RESOURCE** structures containing information about each Resource Instances.</span></span>

- <span data-ttu-id="a5143-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: en flera resurs som definieras av *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="a5143-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="a5143-176">*nx_lwm2m_resource_multiple_ptr* är en pekare till en TLV-kodad buffert.</span><span class="sxs-lookup"><span data-stu-id="a5143-176">*nx_lwm2m_resource_multiple_ptr* is a pointer to a TLV encoded buffer.</span></span>

<span data-ttu-id="a5143-177">Bekvämlighets funktioner används för att hämta värdet och kontrol lera dess typ. programmet ska aldrig direkt komma åt *nx_lwm2m_resource_value* fältet när du hämtar ett värde från en NX_LWM2M_RESOURCE-struktur.</span><span class="sxs-lookup"><span data-stu-id="a5143-177">Convenience functions are provided for retrieving the value and checking its type, the application should never directly access the *nx_lwm2m_resource_value* field when getting a value from a NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="a5143-178">Följande funktioner definieras:</span><span class="sxs-lookup"><span data-stu-id="a5143-178">The following functions are defined :</span></span>

- <span data-ttu-id="a5143-179">***nx_lwm2m_resource_get_***: Hämta ett värde med den aktuella typen.</span><span class="sxs-lookup"><span data-stu-id="a5143-179">***nx_lwm2m_resource_get_***: Get a value with the given type.</span></span>
- <span data-ttu-id="a5143-180">***nx_lwm2m_resource_multiple_get_***: Hämta ett värde med en specifik typ från en flera resurser.</span><span class="sxs-lookup"><span data-stu-id="a5143-180">***nx_lwm2m_resource_multiple_get_***: Get a value with the given type from a Multiple Resource.</span></span>

<span data-ttu-id="a5143-181">Makro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(typ) kan användas för att kontrol lera om en resurs typ är en flera resurser.</span><span class="sxs-lookup"><span data-stu-id="a5143-181">The macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) can be used to check if a resource type is a Multiple Resource.</span></span>

## <a name="object-implementation"></a><span data-ttu-id="a5143-182">Objekt implementering</span><span class="sxs-lookup"><span data-stu-id="a5143-182">Object Implementation</span></span>

<span data-ttu-id="a5143-183">LWM2M-klienten implementerar de obligatoriska OMA LWM2M-objekten: säkerhet (0), Server (1), Access Control (2) och enhet (3).</span><span class="sxs-lookup"><span data-stu-id="a5143-183">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="a5143-184">Andra enhets specifika objekt måste implementeras av programmet.</span><span class="sxs-lookup"><span data-stu-id="a5143-184">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="a5143-185">Två data strukturer används för att definiera ett objekt: NX_LWM2M_OBJECTs strukturen definierar objekt implementeringen, inklusive objekt-ID och objekt metoder, och NX_LWM2M_OBJECT_INSTANCE strukturen innehåller data för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-185">Two data structures are used to define an Object: the NX_LWM2M_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="a5143-186">NX_LWM2M_OBJECTs strukturen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-186">The NX_LWM2M_OBJECT structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- <span data-ttu-id="a5143-187">**nx_lwm2m_object_next**: Nästa objekt i listan.</span><span class="sxs-lookup"><span data-stu-id="a5143-187">**nx_lwm2m_object_next**: The next object in the list.</span></span>
- <span data-ttu-id="a5143-188">**nx_lwm2m_object_id**: objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="a5143-188">**nx_lwm2m_object_id**: The Object ID.</span></span>
- <span data-ttu-id="a5143-189">**nx_lwm2m_object_read**: metoden Read, se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-189">**nx_lwm2m_object_read**: The 'Read' method, see below.</span></span>
- <span data-ttu-id="a5143-190">**nx_lwm2m_object_discover**: ' Discover '-metoden finns nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-190">**nx_lwm2m_object_discover**: The 'Discover' method, see below.</span></span>
- <span data-ttu-id="a5143-191">**nx_lwm2m_object_write**: metoden Write, se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-191">**nx_lwm2m_object_write**: The 'Write' method, see below.</span></span>
- <span data-ttu-id="a5143-192">**nx_lwm2m_object_execute**: metoden Execute, se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-192">**nx_lwm2m_object_execute**: The 'Execute' method, see below.</span></span>
- <span data-ttu-id="a5143-193">**nx_lwm2m_object_create**: metoden ' create ', se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-193">**nx_lwm2m_object_create**: The 'Create' method, see below.</span></span>
- <span data-ttu-id="a5143-194">**nx_lwm2m_object_delete**: metoden Delete, se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-194">**nx_lwm2m_object_delete**: The 'Delete' method, see below.</span></span>
- <span data-ttu-id="a5143-195">**nx_lwm2m_object_instances**: listan över null-terminerade objekt instanser.</span><span class="sxs-lookup"><span data-stu-id="a5143-195">**nx_lwm2m_object_instances**: The NULL-terminated list of object instances.</span></span>

<span data-ttu-id="a5143-196">NX_LWM2M_OBJECT_INSTANCEs strukturen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-196">The NX_LWM2M_OBJECT_INSTANCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- <span data-ttu-id="a5143-197">**nx_lwm2m_object_instance_next**: nästa instans i listan.</span><span class="sxs-lookup"><span data-stu-id="a5143-197">**nx_lwm2m_object_instance_next**: The next instance in the list.</span></span>
- <span data-ttu-id="a5143-198">**nx_lwm2m_object_instance_id**: ID för objekt instans.</span><span class="sxs-lookup"><span data-stu-id="a5143-198">**nx_lwm2m_object_instance_id**: The Object Instance ID.</span></span>

<span data-ttu-id="a5143-199">Objektet måste implementera de metoder som motsvarar de åtgärder som definierats av LWM2M enhets hanterings gränssnitt: Read, Discovery, Write, EXECUTE, Create och Delete.</span><span class="sxs-lookup"><span data-stu-id="a5143-199">The Object must implement the methods corresponding to the operations defined by the LWM2M Device Management Interface: 'Read', 'Discover', 'Write', 'Execute', 'Create' and 'Delete'.</span></span> <span data-ttu-id="a5143-200">Metoderna Create och Delete kan anges till NULL om objektet inte stöder dynamisk generering av instanser.</span><span class="sxs-lookup"><span data-stu-id="a5143-200">The 'Create' and 'Delete' methods can be set to NULL if the object doesn't support dynamic creation of instances.</span></span>

### <a name="the-read-method"></a><span data-ttu-id="a5143-201">Metoden Read</span><span class="sxs-lookup"><span data-stu-id="a5143-201">The 'Read' Method</span></span>

<span data-ttu-id="a5143-202">Metoden Read används för att läsa resurs värden från en objekt instans, funktionen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-202">The 'Read' method is used to read Resource values from an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

<span data-ttu-id="a5143-203">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-203">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="a5143-204">**object_ptr**: pekar mot objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="a5143-204">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="a5143-205">**instance_ptr**: pekar mot objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-205">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="a5143-206">**num_values**: antalet resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="a5143-206">**num_values**: The number of resources to read.</span></span>

- <span data-ttu-id="a5143-207">**values_ptr**: pekar mot en matris med NX_LWM2M_RESOURCE som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="a5143-207">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="a5143-208">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="a5143-208">On return the array is filled with the corresponding types and values.</span></span>

### <a name="the-discover-method"></a><span data-ttu-id="a5143-209">Identifiera-metoden</span><span class="sxs-lookup"><span data-stu-id="a5143-209">The 'Discover' Method</span></span>

<span data-ttu-id="a5143-210">Identifiera-metoden används för att hämta en lista över alla resurser som implementerats av ett objekt, funktionen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-210">The 'Discover' method is used to retrieve the list of all Resources implemented by an Object, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

<span data-ttu-id="a5143-211">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-211">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="a5143-212">**object_ptr**: pekar mot objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="a5143-212">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="a5143-213">**instance_ptr**: pekar mot objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-213">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="a5143-214">**num_resources_ptr**: om du vill ange storleken på måldomänkontrollanten vid utdata anger du antalet element som skrivs till bufferten.</span><span class="sxs-lookup"><span data-stu-id="a5143-214">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>

- <span data-ttu-id="a5143-215">**resources_ptr**: pekar mot målcachen.</span><span class="sxs-lookup"><span data-stu-id="a5143-215">**resources_ptr**: Pointer to the destination buffer.</span></span>

<span data-ttu-id="a5143-216">Resursinformationen returneras i en NX_LWM2M_RESOURCE_INFO-struktur som definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-216">The resource information is returned in a NX_LWM2M_RESOURCE_INFO structure defined as follows:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- <span data-ttu-id="a5143-217">**nx_lwm2m_resource_info_id**: resursens ID.</span><span class="sxs-lookup"><span data-stu-id="a5143-217">**nx_lwm2m_resource_info_id**: The ID of the Resource.</span></span>

- <span data-ttu-id="a5143-218">**nx_lwm2m_resource_info_flags**: se nedan.</span><span class="sxs-lookup"><span data-stu-id="a5143-218">**nx_lwm2m_resource_info_flags**: See below.</span></span>

- <span data-ttu-id="a5143-219">**nx_lwm2m_resource_info_dim**: dimensionen för flera resurser om flaggan NX_LWM2M_RESOURCE_INFO_MULTIPLE har angetts.</span><span class="sxs-lookup"><span data-stu-id="a5143-219">**nx_lwm2m_resource_info_dim**: The dimension of Multiple Resource if the flag NX_LWM2M_RESOURCE_INFO_MULTIPLE is set.</span></span>

<span data-ttu-id="a5143-220">Fältet *nx_lwm2m_resource_flags* kan ha följande värden:</span><span class="sxs-lookup"><span data-stu-id="a5143-220">The field *nx_lwm2m_resource_flags* can have to the following values:</span></span>

- <span data-ttu-id="a5143-221">0: en läsbar resurs.</span><span class="sxs-lookup"><span data-stu-id="a5143-221">0: Single readable resource.</span></span>

- <span data-ttu-id="a5143-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: flera resurser måste *nx_lwm2m_resource_info_dim* definieras.</span><span class="sxs-lookup"><span data-stu-id="a5143-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: Multiple Resource, *nx_lwm2m_resource_info_dim* must be defined.</span></span>

- <span data-ttu-id="a5143-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: körbar eller icke läsbar resurs.</span><span class="sxs-lookup"><span data-stu-id="a5143-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: Executable or Non-Readable Resource.</span></span>

### <a name="the-write-method"></a><span data-ttu-id="a5143-224">Write-metoden</span><span class="sxs-lookup"><span data-stu-id="a5143-224">The 'Write' Method</span></span>

<span data-ttu-id="a5143-225">Metoden Write används för att uppdatera eller ersätta resurser för en objekt instans, funktionen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-225">The 'Write' method is used to update or replace resources of an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

<span data-ttu-id="a5143-226">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-226">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="a5143-227">**object_ptr**: pekar mot objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="a5143-227">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="a5143-228">**instance_ptr**: pekar mot objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-228">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="a5143-229">**num_values**: antalet resurser som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="a5143-229">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="a5143-230">**values_ptr**: pekar mot resurs värden.</span><span class="sxs-lookup"><span data-stu-id="a5143-230">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="a5143-231">**write_op**: typ av Skriv åtgärder.</span><span class="sxs-lookup"><span data-stu-id="a5143-231">**write_op**: The type of write operations.</span></span>

<span data-ttu-id="a5143-232">Följande Skriv åtgärder kan anges för parametern *write_op* :</span><span class="sxs-lookup"><span data-stu-id="a5143-232">The following write operations can be specified to the *write_op* parameter :</span></span>

- <span data-ttu-id="a5143-233">0 &mdash; del uppdatering: lägger till eller uppdaterar resurser som finns i det nya värdet och låter andra befintliga resurser ändras,</span><span class="sxs-lookup"><span data-stu-id="a5143-233">0 &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="a5143-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Ersätt instans: ersätter objekt instansen med de nya angivna resurs värdena.</span><span class="sxs-lookup"><span data-stu-id="a5143-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="a5143-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Ersätt resurs: ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser).</span><span class="sxs-lookup"><span data-stu-id="a5143-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="a5143-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Skapa instans: initierar den nyligen skapade objekt instansen med de tillhandahållna resurs värdena (anropades från metoden *nx_lwm2m_object_create* ).</span><span class="sxs-lookup"><span data-stu-id="a5143-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: initializes the newly created Object Instance with the provided resource values (called from the *nx_lwm2m_object_create* method).</span></span>

- <span data-ttu-id="a5143-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap-skrivning: anropas under bootstrap-sekvens.</span><span class="sxs-lookup"><span data-stu-id="a5143-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: called during Bootstrap sequence.</span></span>

### <a name="the-execute-method"></a><span data-ttu-id="a5143-238">Metoden Execute</span><span class="sxs-lookup"><span data-stu-id="a5143-238">The 'Execute' Method</span></span>

<span data-ttu-id="a5143-239">Metoden Execute implementerar körningen av en objekt resurs, funktionen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-239">The 'Execute' method implements the execution of an Object Resource, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

<span data-ttu-id="a5143-240">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-240">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="a5143-241">**object_ptr**: pekar mot objekt implementeringen</span><span class="sxs-lookup"><span data-stu-id="a5143-241">**object_ptr**: Pointer to the Object implementation</span></span>
- <span data-ttu-id="a5143-242">**instance_ptr**: pekar mot objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-242">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="a5143-243">**resource_id**: resurs-ID.</span><span class="sxs-lookup"><span data-stu-id="a5143-243">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="a5143-244">**arguments_ptr**: pekar mot argumenten för körnings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a5143-244">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="a5143-245">Kan vara NULL om *arguments_length* är noll.</span><span class="sxs-lookup"><span data-stu-id="a5143-245">Can be NULL if *arguments_length* is zero.</span></span>
- <span data-ttu-id="a5143-246">**arguments_length**: argumentens längd.</span><span class="sxs-lookup"><span data-stu-id="a5143-246">**arguments_length**: The length of the arguments.</span></span>

<span data-ttu-id="a5143-247">Funktionen måste returnera NX_LWM2M_NOT_FOUND om resurs-ID: t inte finns eller NX_LWM2M_METHOD_NOT_ALLOWED om det inte stöder körning.</span><span class="sxs-lookup"><span data-stu-id="a5143-247">The function must return NX_LWM2M_NOT_FOUND if the Resource ID doesn't exist, or NX_LWM2M_METHOD_NOT_ALLOWED if it doesn't support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="a5143-248">Metoden Create</span><span class="sxs-lookup"><span data-stu-id="a5143-248">The 'Create' Method</span></span>

<span data-ttu-id="a5143-249">Metoden Create implementerar skapandet av en ny objekt instans, funktionen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-249">The 'Create' method implements the creation of a new Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

<span data-ttu-id="a5143-250">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-250">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="a5143-251">**object_ptr**: pekar mot objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="a5143-251">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="a5143-252">**instance_id**: ID för den nya instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-252">**instance_id**: The ID of the new Instance.</span></span>
- <span data-ttu-id="a5143-253">**num_values**: antalet resurser som ska initieras.</span><span class="sxs-lookup"><span data-stu-id="a5143-253">**num_values**: The number of resources to initialize.</span></span>
- <span data-ttu-id="a5143-254">**values_ptr**: pekar mot resurs värden.</span><span class="sxs-lookup"><span data-stu-id="a5143-254">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="a5143-255">**instance_ptr**: pekar mot destinations pekaren för den skapade instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-255">**instance_ptr**: Pointer to the destination pointer of the created instance.</span></span>
- <span data-ttu-id="a5143-256">**bootstrap**: true om den anropas från bootstrap-sekvens.</span><span class="sxs-lookup"><span data-stu-id="a5143-256">**bootstrap**: True if called from bootstrap sequence.</span></span>

<span data-ttu-id="a5143-257">Objektet måste allokera och initialiaze en ny objekt instans med hjälp av den angivna listan med resurs värden.</span><span class="sxs-lookup"><span data-stu-id="a5143-257">The Object must allocate and initialiaze a new Object instance, using the provided list of resource values.</span></span>

### <a name="the-delete-method"></a><span data-ttu-id="a5143-258">Metoden Delete</span><span class="sxs-lookup"><span data-stu-id="a5143-258">The 'Delete' Method</span></span>

<span data-ttu-id="a5143-259">Metoden Delete implementerar borttagningen av en objekt instans, funktionen har följande definition:</span><span class="sxs-lookup"><span data-stu-id="a5143-259">The 'Delete' method implements the deletion of an object instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

<span data-ttu-id="a5143-260">Indataparametrarna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a5143-260">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="a5143-261">**object_ptr**: pekar mot objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="a5143-261">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="a5143-262">**instance_ptr**: pekar mot objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-262">**instance_ptr**: Pointer to the Object Instance.</span></span>

<span data-ttu-id="a5143-263">Vid lyckad måste objektet frisläppa objekt instans data och andra resurser som allokerats av instansen.</span><span class="sxs-lookup"><span data-stu-id="a5143-263">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a><span data-ttu-id="a5143-264">Lägga till objekt implementeringar och instanser i LWM2M-klienten</span><span class="sxs-lookup"><span data-stu-id="a5143-264">Adding Object Implementations and Instances to the LWM2M Client</span></span>

<span data-ttu-id="a5143-265">Programmet kan lägga till ny objekt implementering i LWM2M-klienten genom att anropa tjänsten ***nx_lwm2m_client_object_add*** .</span><span class="sxs-lookup"><span data-stu-id="a5143-265">The application can add new object implementation to the LWM2M Client by calling the ***nx_lwm2m_client_object_add*** service.</span></span>

<span data-ttu-id="a5143-266">Om objektet inte stöder dynamisk skapande av instanser, till exempel om det är ett enda instans objekt, ska *nx_lwm2m_object_instances* fältet i objekt strukturen peka på listan över de statiska instans strukturerna.</span><span class="sxs-lookup"><span data-stu-id="a5143-266">If the Object doesn't support dynamic creation of Instances, for example if it's a single instance only Object, the *nx_lwm2m_object_instances* field of the object structure should point to the list of the static instances structures.</span></span>

<span data-ttu-id="a5143-267">Om objektet har stöd för att skapa dynamiska instanser måste *nx_lwm2m_object_instances* vara inställt på NULL och ***nx_lwm2m_client_object_creates*** tjänsten ska användas i stället för att anropa "Create"-metoden för objektet.</span><span class="sxs-lookup"><span data-stu-id="a5143-267">If the Object supports dynamic instance creation, *nx_lwm2m_object_instances* should be set to NULL and the ***nx_lwm2m_client_object_create*** service should be used instead in order to call the 'Create' method of the object.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="a5143-268">Exempel på LWM2M-klientprogram</span><span class="sxs-lookup"><span data-stu-id="a5143-268">Example of LWM2M Client Application</span></span>

<span data-ttu-id="a5143-269">Följande kod är ett exempel på ett enkelt LWM2M klient program som implementerar en anpassad enhet som består av en temperatur sensor och en ljus växel.</span><span class="sxs-lookup"><span data-stu-id="a5143-269">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="a5143-270">Enheten gör att en server kan läsa värdet för temperatur sensorn och den booleska statusen för ljus växeln och för att ställa in ljus växeln på/av.</span><span class="sxs-lookup"><span data-stu-id="a5143-270">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
