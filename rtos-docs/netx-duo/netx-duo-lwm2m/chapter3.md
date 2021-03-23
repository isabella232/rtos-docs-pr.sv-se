---
title: Kapitel 3 – funktions Beskrivning av LWM2M-klienten
description: Det här kapitlet innehåller en funktions Beskrivning av LWM2M-klienten.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825938"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="073f5-103">Kapitel 3 funktions Beskrivning av LWM2M-klienten</span><span class="sxs-lookup"><span data-stu-id="073f5-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="073f5-104">Det här kapitlet innehåller en funktions Beskrivning av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="073f5-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="073f5-105">LWM2M klient initiering</span><span class="sxs-lookup"><span data-stu-id="073f5-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="073f5-106">LWM2M-klienten initieras genom att anropa ***nx_lwm2m_client_creates*** tjänsten.</span><span class="sxs-lookup"><span data-stu-id="073f5-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="073f5-107">LWM2M-klienten körs i sin egen tråd och kan rapportera vissa händelser till programmet genom att använda återanrop eller genom att anropa metoder för de anpassade objekt som implementeras av programmet.</span><span class="sxs-lookup"><span data-stu-id="073f5-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="073f5-108">Dessutom måste LWM2M-klientsessioner skapas genom att anropa ***nx_lwm2m_client_session_create*** för att aktivera kommunikation med en eller flera servrar.</span><span class="sxs-lookup"><span data-stu-id="073f5-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="073f5-109">En session kan kommunicera med två olika typer av servrar: en Start Server eller en LWM2M-Server (enhets hantering).</span><span class="sxs-lookup"><span data-stu-id="073f5-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="073f5-110">Bootstrap-Server-session</span><span class="sxs-lookup"><span data-stu-id="073f5-110">Bootstrap Server Session</span></span>

<span data-ttu-id="073f5-111">En kommunikations-session med en Start Server används för att tillhandahålla viktig information till LWM2M-klienten så att LWM2M-klienten kan utföra åtgärden "Registrera" med en eller flera LWM2M-servrar.</span><span class="sxs-lookup"><span data-stu-id="073f5-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="073f5-112">Den här typen av Server används vid start läge för klienten som initierats och initierats av servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="073f5-113">Programmet kan starta en bootstrap-session genom att anropa ***nx_lwm2m_client_session_bootstrap** _ eller _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, den måste ange IP-adressen och port numret för-servern och ett valfritt säkerhets objekts instans-ID.</span><span class="sxs-lookup"><span data-stu-id="073f5-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="073f5-114">Funktionen _*_nx_lwm2m_client_session_bootstrap_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* upprättar en säker DTLS-anslutning till servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="073f5-115">Om bootstrap-åtgärden lyckas ska start servern ha skapat säkerhets objekts instanser för start-och LWM2M-servrarna och Server objekt instanser för LWM2M-servrarna.</span><span class="sxs-lookup"><span data-stu-id="073f5-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="073f5-116">Programmet kan anropa ***nx_lwm2m_client_session_register_info_get*** för att hämta information om Lwm2m-servrar och använda den här informationen för att upprätta en session med Lwm2m-servrarna.</span><span class="sxs-lookup"><span data-stu-id="073f5-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="073f5-117">Bootstrap-data ska sparas till beständigt minne av programmet för att konfigurera LWM2M-klienten vid nästa omstart av enheten.</span><span class="sxs-lookup"><span data-stu-id="073f5-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="073f5-118">LWM2M Server-session</span><span class="sxs-lookup"><span data-stu-id="073f5-118">LWM2M Server Session</span></span>

<span data-ttu-id="073f5-119">En kommunikations-session med en LWM2M-Server används för registrering, enhets hantering och tjänst aktivering.</span><span class="sxs-lookup"><span data-stu-id="073f5-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="073f5-120">Programmet kan registrera LWM2M-klienten på en server genom att anropa ***nx_lwm2m_client_session_register** _ eller _*_nx_lwm2m_client_session_register_dtls_\*_, den måste ange IP-adressen och port numret för-servern och det korta Server-ID som motsvarar en befintlig server objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="073f5-121">Funktionen _*_nx_lwm2m_client_session_register_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_register_dtls_*\* upprättar en säker DTLS-anslutning till servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="073f5-122">Programmet kan avregistrera LWM2M-klienten genom att anropa \***nx_lwm2m_client_session_deregister** _ och be klienten att skicka ett uppdaterings meddelande genom att anropa _ *_nx_lwm2m_client_session_update_* \*.</span><span class="sxs-lookup"><span data-stu-id="073f5-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="073f5-123">Motanrop för sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="073f5-123">Session State Callback</span></span>

<span data-ttu-id="073f5-124">Programmet registrerar ett återanrop vid skapandet av en session som anropas när sessionens status uppdateras. motringningsfunktionen **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** har följande prototyp.</span><span class="sxs-lookup"><span data-stu-id="073f5-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="073f5-125">TypeDef VOID ( \* NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK) (NX_LWM2M_CLIENT_SESSION \* SESSION_PTR, uint-tillstånd);</span><span class="sxs-lookup"><span data-stu-id="073f5-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="073f5-126">Följande tillstånd definieras.</span><span class="sxs-lookup"><span data-stu-id="073f5-126">The following states are defined.</span></span>

| <span data-ttu-id="073f5-127">Sessionstillstånd &nbsp;</span><span class="sxs-lookup"><span data-stu-id="073f5-127">Session&nbsp;State</span></span> | <span data-ttu-id="073f5-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="073f5-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="073f5-130">Initialt tillstånd efter att sessionen skapats.</span><span class="sxs-lookup"><span data-stu-id="073f5-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="073f5-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="073f5-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="073f5-132">Klienten väntar på att start av timer eller initierad Server ska startas.</span><span class="sxs-lookup"><span data-stu-id="073f5-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="073f5-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="073f5-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="073f5-134">Klienten har skickat ett "Request"-meddelande till bootstrap-servern (klienten initierade start).</span><span class="sxs-lookup"><span data-stu-id="073f5-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="073f5-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="073f5-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="073f5-136">Klienten tar emot data från start servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="073f5-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="073f5-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="073f5-138">Start servern har skickat ett meddelande om att det har skickats.</span><span class="sxs-lookup"><span data-stu-id="073f5-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="073f5-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="073f5-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="073f5-140">Det gick inte att starta bootstrap-sessionen.</span><span class="sxs-lookup"><span data-stu-id="073f5-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="073f5-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="073f5-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="073f5-142">Klienten har skickat ett "Registrera"-meddelande till LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="073f5-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="073f5-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="073f5-144">Klienten är registrerad på LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="073f5-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="073f5-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="073f5-146">Klienten har skickat ett uppdaterings meddelande till LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="073f5-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="073f5-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="073f5-148">Klienten har skickat meddelandet "avregistrera" till LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="073f5-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="073f5-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="073f5-150">Klienten är avregistrerad från LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="073f5-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="073f5-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="073f5-152">LWM2M-servern är inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="073f5-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="073f5-153">En "Registrera" skickas när den inaktiverade timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="073f5-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="073f5-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="073f5-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="073f5-155">Det gick inte att utföra registreringen eller uppdateringen på LWM2M-servern.</span><span class="sxs-lookup"><span data-stu-id="073f5-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="073f5-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="073f5-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="073f5-157">Server objekts instansen som motsvarar LWM2M-servern har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="073f5-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="073f5-158">Om ett fel uppstår kan programmet Hämta orsaken till felet genom att anropa ***nx_lwm2m_client_session_error_get***.</span><span class="sxs-lookup"><span data-stu-id="073f5-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="073f5-159">Hantering av lokala enheter</span><span class="sxs-lookup"><span data-stu-id="073f5-159">Local Device Management</span></span>

<span data-ttu-id="073f5-160">Programmet kan komma åt objekten i LWM2M-klienten med hjälp av funktionerna för lokal enhets hantering.</span><span class="sxs-lookup"><span data-stu-id="073f5-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="073f5-161">Följande funktioner finns.</span><span class="sxs-lookup"><span data-stu-id="073f5-161">The following functions are provided.</span></span>

| <span data-ttu-id="073f5-162">Funktions &nbsp; namn</span><span class="sxs-lookup"><span data-stu-id="073f5-162">Function&nbsp;Name</span></span> | <span data-ttu-id="073f5-163">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="073f5-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="073f5-165">Läsa resurser från en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="073f5-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="073f5-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="073f5-167">Hämta listan över resurser för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="073f5-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="073f5-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="073f5-169">Skriv resurser till en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="073f5-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="073f5-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="073f5-171">Utför åtgärden kör på en resurs av en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="073f5-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="073f5-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="073f5-173">Skapa en ny objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="073f5-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="073f5-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="073f5-175">Ta bort en befintlig objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="073f5-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="073f5-177">Hämta nästa objekt-ID av LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="073f5-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="073f5-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="073f5-179">Hämta nästa instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="073f5-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="073f5-180">Resursinformation</span><span class="sxs-lookup"><span data-stu-id="073f5-180">Resource Information</span></span>

<span data-ttu-id="073f5-181">Vid läsning från och skrivning till objekt representeras en resurs av NX_LWM2M_CLIENT_RESOURCE-strukturen.</span><span class="sxs-lookup"><span data-stu-id="073f5-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="073f5-182">Den här strukturen innehåller ID: t för resursen/instansen och dess värde.</span><span class="sxs-lookup"><span data-stu-id="073f5-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="073f5-183">Följande funktioner finns för att ange resursinformation och-värde.</span><span class="sxs-lookup"><span data-stu-id="073f5-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="073f5-184">Funktions &nbsp; namn</span><span class="sxs-lookup"><span data-stu-id="073f5-184">Function&nbsp;Name</span></span> | <span data-ttu-id="073f5-185">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="073f5-187">Ange resursinformation: resurs-ID och åtgärd: läsa, skriva, KÖRBAR fil.</span><span class="sxs-lookup"><span data-stu-id="073f5-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="073f5-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="073f5-189">Ange resurs värde som sträng.</span><span class="sxs-lookup"><span data-stu-id="073f5-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="073f5-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="073f5-191">Ange resurs värde som 32-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="073f5-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="073f5-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="073f5-193">Ange resurs värde som 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="073f5-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="073f5-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="073f5-195">Ange resurs värde som 32-bitars flyttal.</span><span class="sxs-lookup"><span data-stu-id="073f5-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="073f5-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="073f5-197">Ange resurs värde som 64-bitars flyttal.</span><span class="sxs-lookup"><span data-stu-id="073f5-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="073f5-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="073f5-199">Ange resurs värde som Boolean.</span><span class="sxs-lookup"><span data-stu-id="073f5-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="073f5-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="073f5-201">Ange resurs värde som objekt länk.</span><span class="sxs-lookup"><span data-stu-id="073f5-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="073f5-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="073f5-203">Ange resurs värde som ogenomskinligt.</span><span class="sxs-lookup"><span data-stu-id="073f5-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="073f5-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="073f5-205">Ange resurs värde som instansen för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="073f5-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="073f5-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="073f5-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="073f5-207">Ange resurs dimensionen för flera resurser för identifiering.</span><span class="sxs-lookup"><span data-stu-id="073f5-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="073f5-208">Följande funktioner är tillgängliga för att hämta resurs information och-värde.</span><span class="sxs-lookup"><span data-stu-id="073f5-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="073f5-209">Funktions &nbsp; namn</span><span class="sxs-lookup"><span data-stu-id="073f5-209">Function&nbsp;Name</span></span> | <span data-ttu-id="073f5-210">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="073f5-212">Hämta resurs information: resurs-ID och åtgärd: läsa, skriva, KÖRBAR fil.</span><span class="sxs-lookup"><span data-stu-id="073f5-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="073f5-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="073f5-214">Hämta värdet för en sträng resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="073f5-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="073f5-216">Hämta värdet för en 32-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="073f5-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="073f5-218">Hämta värdet för en B4-bitars heltals resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="073f5-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="073f5-220">Hämta värdet för en 32-bitars float-resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="073f5-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="073f5-222">Hämta värdet för en 64-bitars float-resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="073f5-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="073f5-224">Hämta värdet för en boolesk resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="073f5-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="073f5-226">Hämta värdet för en objekt länk resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="073f5-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="073f5-228">Hämta värdet för en ogenomskinlig resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="073f5-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="073f5-230">Hämta resurs instansen för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="073f5-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="073f5-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="073f5-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="073f5-232">Hämta resurs dimensionen för flera resurser.</span><span class="sxs-lookup"><span data-stu-id="073f5-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="073f5-233">Objekt implementering</span><span class="sxs-lookup"><span data-stu-id="073f5-233">Object Implementation</span></span>

<span data-ttu-id="073f5-234">LWM2M-klienten implementerar de obligatoriska OMA LWM2M-objekten: säkerhet (0), Server (1), Access Control (2) och enhet (3).</span><span class="sxs-lookup"><span data-stu-id="073f5-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="073f5-235">Andra enhets specifika objekt måste implementeras av programmet.</span><span class="sxs-lookup"><span data-stu-id="073f5-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="073f5-236">Två data strukturer används för att definiera ett objekt: NX_LWM2M_CLIENT_OBJECTs strukturen definierar objekt implementeringen, inklusive objekt-ID och objekt metoder, och NX_LWM2M_CLIENT_OBJECT_INSTANCE strukturen innehåller data för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="073f5-237">Följande funktioner finns.</span><span class="sxs-lookup"><span data-stu-id="073f5-237">The following functions are provided.</span></span>

| <span data-ttu-id="073f5-238">Funktions &nbsp; namn</span><span class="sxs-lookup"><span data-stu-id="073f5-238">Function&nbsp;Name</span></span> | <span data-ttu-id="073f5-239">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="073f5-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="073f5-241">Lägg till objekt implementering i LwM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="073f5-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="073f5-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="073f5-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="073f5-243">Ta bort objekt implementering från LwM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="073f5-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="073f5-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="073f5-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="073f5-245">Lägg till objekt instans i objektet.</span><span class="sxs-lookup"><span data-stu-id="073f5-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="073f5-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="073f5-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="073f5-247">Ta bort objekt instansen från objektet.</span><span class="sxs-lookup"><span data-stu-id="073f5-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="073f5-248">Funktionen callback för objekt metod innehåller en signatur som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="073f5-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="073f5-249">Metoden Read</span><span class="sxs-lookup"><span data-stu-id="073f5-249">The ‘Read’ Method</span></span>

<span data-ttu-id="073f5-250">Metoden Read används för att läsa resurs värden från en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="073f5-251">Parametrarna definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="073f5-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="073f5-252">Parameter</span><span class="sxs-lookup"><span data-stu-id="073f5-252">Parameter</span></span> | <span data-ttu-id="073f5-253">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-254">**reparation**</span><span class="sxs-lookup"><span data-stu-id="073f5-254">**operation**</span></span> | <span data-ttu-id="073f5-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="073f5-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="073f5-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-256">**object_ptr**</span></span> | <span data-ttu-id="073f5-257">Pekare till objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="073f5-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="073f5-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-258">**instance_ptr**</span></span> | <span data-ttu-id="073f5-259">Pekare till objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="073f5-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="073f5-260">**klusterresursen**</span><span class="sxs-lookup"><span data-stu-id="073f5-260">**resource**</span></span> | <span data-ttu-id="073f5-261">Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="073f5-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="073f5-262">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="073f5-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="073f5-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="073f5-263">**resource_count**</span></span> | <span data-ttu-id="073f5-264">Pekar på antalet resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="073f5-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="073f5-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-265">**args_ptr**</span></span> | <span data-ttu-id="073f5-266">Oanvänd parameter för läsning.</span><span class="sxs-lookup"><span data-stu-id="073f5-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="073f5-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="073f5-267">**args_length**</span></span> | <span data-ttu-id="073f5-268">Oanvänd parameter för läsning.</span><span class="sxs-lookup"><span data-stu-id="073f5-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="073f5-269">Identifiera-metoden</span><span class="sxs-lookup"><span data-stu-id="073f5-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="073f5-270">Identifiera-metoden används för att hämta en lista över alla resurser som implementerats av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="073f5-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="073f5-271">Parametrarna definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="073f5-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="073f5-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="073f5-272">Parameter</span></span> | <span data-ttu-id="073f5-273">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-274">**reparation**</span><span class="sxs-lookup"><span data-stu-id="073f5-274">**operation**</span></span> | <span data-ttu-id="073f5-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="073f5-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="073f5-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-276">**object_ptr**</span></span> | <span data-ttu-id="073f5-277">Pekare till objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="073f5-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="073f5-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-278">**instance_ptr**</span></span> | <span data-ttu-id="073f5-279">Pekare till objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="073f5-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="073f5-280">**klusterresursen**</span><span class="sxs-lookup"><span data-stu-id="073f5-280">**resource**</span></span> | <span data-ttu-id="073f5-281">Pekare till en matris med NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="073f5-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="073f5-282">Vid retur fylls matrisen med motsvarande resursinformation.</span><span class="sxs-lookup"><span data-stu-id="073f5-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="073f5-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="073f5-283">**resource_count**</span></span> | <span data-ttu-id="073f5-284">Pekar på antalet resurser som ska identifieras.</span><span class="sxs-lookup"><span data-stu-id="073f5-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="073f5-285">Vid retur måste den här parametern uppdateras som det sanna värdet.</span><span class="sxs-lookup"><span data-stu-id="073f5-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="073f5-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-286">**args_ptr**</span></span> | <span data-ttu-id="073f5-287">Oanvänd parameter för identifiering.</span><span class="sxs-lookup"><span data-stu-id="073f5-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="073f5-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="073f5-288">**args_length**</span></span> | <span data-ttu-id="073f5-289">Oanvänd parameter för identifiering.</span><span class="sxs-lookup"><span data-stu-id="073f5-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="073f5-290">Write-metoden</span><span class="sxs-lookup"><span data-stu-id="073f5-290">The ‘Write’ Method</span></span>

<span data-ttu-id="073f5-291">Metoden Write används för att uppdatera eller ersätta resurser för en objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="073f5-292">Parametrarna definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="073f5-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="073f5-293">Parameter</span><span class="sxs-lookup"><span data-stu-id="073f5-293">Parameter</span></span>  | <span data-ttu-id="073f5-294">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-295">**reparation**</span><span class="sxs-lookup"><span data-stu-id="073f5-295">**operation**</span></span> | <span data-ttu-id="073f5-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="073f5-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="073f5-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-297">**object_ptr**</span></span> | <span data-ttu-id="073f5-298">Pekare till objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="073f5-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="073f5-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-299">**instance_ptr**</span></span> | <span data-ttu-id="073f5-300">Pekare till objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="073f5-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="073f5-301">**klusterresursen**</span><span class="sxs-lookup"><span data-stu-id="073f5-301">**resource**</span></span> | <span data-ttu-id="073f5-302">Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="073f5-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="073f5-303">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="073f5-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="073f5-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="073f5-304">**resource_count**</span></span> | <span data-ttu-id="073f5-305">Pekar på antalet resurser som ska identifieras.</span><span class="sxs-lookup"><span data-stu-id="073f5-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="073f5-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-306">**args_ptr**</span></span> | <span data-ttu-id="073f5-307">Skriv flaggor.</span><span class="sxs-lookup"><span data-stu-id="073f5-307">Write flags.</span></span> |
| <span data-ttu-id="073f5-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="073f5-308">**args_length**</span></span> | <span data-ttu-id="073f5-309">Argumentens längd.</span><span class="sxs-lookup"><span data-stu-id="073f5-309">The length of the arguments.</span></span> |

<span data-ttu-id="073f5-310">Följande Skriv åtgärder kan anges för *flagg* parametern.</span><span class="sxs-lookup"><span data-stu-id="073f5-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="073f5-311">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="073f5-311">Operation</span></span> | <span data-ttu-id="073f5-312">Åtgärd</span><span class="sxs-lookup"><span data-stu-id="073f5-312">Action</span></span> | <span data-ttu-id="073f5-313">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="073f5-314">0</span><span class="sxs-lookup"><span data-stu-id="073f5-314">0</span></span> | <span data-ttu-id="073f5-315">Partiell uppdatering</span><span class="sxs-lookup"><span data-stu-id="073f5-315">Partial Update</span></span> | <span data-ttu-id="073f5-316">Lägger till eller uppdaterar resurser som finns i det nya värdet och lämnar andra befintliga resurser oförändrade.</span><span class="sxs-lookup"><span data-stu-id="073f5-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="073f5-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="073f5-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="073f5-318">Ersätt instans</span><span class="sxs-lookup"><span data-stu-id="073f5-318">Replace Instance</span></span> | <span data-ttu-id="073f5-319">Ersätter objekt instansen med de nya angivna resurs värdena.</span><span class="sxs-lookup"><span data-stu-id="073f5-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="073f5-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="073f5-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="073f5-321">Ersätt resurs</span><span class="sxs-lookup"><span data-stu-id="073f5-321">Replace Resource</span></span> | <span data-ttu-id="073f5-322">Ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser).</span><span class="sxs-lookup"><span data-stu-id="073f5-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="073f5-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="073f5-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="073f5-324">Skapa instans</span><span class="sxs-lookup"><span data-stu-id="073f5-324">Create Instance</span></span> | <span data-ttu-id="073f5-325">Initierar den nyligen skapade objekt instansen med de tillhandahållna resurs värdena (anropas från metoden **_nx_lwm2m_object_create_** ).</span><span class="sxs-lookup"><span data-stu-id="073f5-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="073f5-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="073f5-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="073f5-327">Bootstrap-skrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-327">Bootstrap Write</span></span> | <span data-ttu-id="073f5-328">Anropas under bootstrap-sekvens.</span><span class="sxs-lookup"><span data-stu-id="073f5-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="073f5-329">Metoden Execute</span><span class="sxs-lookup"><span data-stu-id="073f5-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="073f5-330">Metoden Execute implementerar körningen av en objekt resurs.</span><span class="sxs-lookup"><span data-stu-id="073f5-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="073f5-331">Indataparametrarna definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="073f5-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="073f5-332">Parameter</span><span class="sxs-lookup"><span data-stu-id="073f5-332">Parameter</span></span>  | <span data-ttu-id="073f5-333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-334">**reparation**</span><span class="sxs-lookup"><span data-stu-id="073f5-334">**operation**</span></span> | <span data-ttu-id="073f5-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="073f5-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="073f5-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-336">**object_ptr**</span></span> | <span data-ttu-id="073f5-337">Pekare till objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="073f5-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="073f5-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-338">**instance_ptr**</span></span> | <span data-ttu-id="073f5-339">Pekare till objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="073f5-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="073f5-340">**klusterresursen**</span><span class="sxs-lookup"><span data-stu-id="073f5-340">**resource**</span></span> | <span data-ttu-id="073f5-341">Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="073f5-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="073f5-342">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="073f5-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="073f5-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="073f5-343">**resource_count**</span></span> | <span data-ttu-id="073f5-344">Pekar på antalet resurser som ska identifieras.</span><span class="sxs-lookup"><span data-stu-id="073f5-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="073f5-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-345">**args_ptr**</span></span> | <span data-ttu-id="073f5-346">Pekar mot argumenten.</span><span class="sxs-lookup"><span data-stu-id="073f5-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="073f5-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="073f5-347">**args_length**</span></span> | <span data-ttu-id="073f5-348">Argumentens längd.</span><span class="sxs-lookup"><span data-stu-id="073f5-348">The length of the arguments.</span></span>  |

<span data-ttu-id="073f5-349">Funktionen måste returnera **NX_LWM2M_CLIENT_NOT_FOUND** om resurs-ID: t inte finns eller **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** om det inte stöder körning.</span><span class="sxs-lookup"><span data-stu-id="073f5-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="073f5-350">Metoden Create</span><span class="sxs-lookup"><span data-stu-id="073f5-350">The ‘Create’ Method</span></span>

<span data-ttu-id="073f5-351">Metoden Create implementerar skapandet av en ny objekt instans.</span><span class="sxs-lookup"><span data-stu-id="073f5-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="073f5-352">Indataparametrarna definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="073f5-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="073f5-353">Parameter</span><span class="sxs-lookup"><span data-stu-id="073f5-353">Parameter</span></span>  | <span data-ttu-id="073f5-354">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-355">**reparation**</span><span class="sxs-lookup"><span data-stu-id="073f5-355">**operation**</span></span> | <span data-ttu-id="073f5-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="073f5-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="073f5-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-357">**object_ptr**</span></span> | <span data-ttu-id="073f5-358">Pekare till objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="073f5-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="073f5-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-359">**instance_ptr**</span></span> | <span data-ttu-id="073f5-360">Oanvänd parameter.</span><span class="sxs-lookup"><span data-stu-id="073f5-360">Unused parameter.</span></span> |
| <span data-ttu-id="073f5-361">**klusterresursen**</span><span class="sxs-lookup"><span data-stu-id="073f5-361">**resource**</span></span> | <span data-ttu-id="073f5-362">Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="073f5-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="073f5-363">Vid retur fylls matrisen med motsvarande typer och värden.</span><span class="sxs-lookup"><span data-stu-id="073f5-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="073f5-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="073f5-364">**resource_count**</span></span> | <span data-ttu-id="073f5-365">Pekar på antalet resurser som ska identifieras.</span><span class="sxs-lookup"><span data-stu-id="073f5-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="073f5-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-366">**args_ptr**</span></span> | <span data-ttu-id="073f5-367">Objekt instans-ID.</span><span class="sxs-lookup"><span data-stu-id="073f5-367">Object instance id.</span></span> |
| <span data-ttu-id="073f5-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="073f5-368">**args_length**</span></span> | <span data-ttu-id="073f5-369">Argumentens längd.</span><span class="sxs-lookup"><span data-stu-id="073f5-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="073f5-370">Metoden Delete</span><span class="sxs-lookup"><span data-stu-id="073f5-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="073f5-371">Metoden Delete implementerar borttagningen av en objekt instans, indataparametrarna definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="073f5-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="073f5-372">Parameter</span><span class="sxs-lookup"><span data-stu-id="073f5-372">Parameter</span></span>  | <span data-ttu-id="073f5-373">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="073f5-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="073f5-374">**reparation**</span><span class="sxs-lookup"><span data-stu-id="073f5-374">**operation**</span></span> | <span data-ttu-id="073f5-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="073f5-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="073f5-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-376">**object_ptr**</span></span> | <span data-ttu-id="073f5-377">Pekare till objekt implementeringen.</span><span class="sxs-lookup"><span data-stu-id="073f5-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="073f5-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-378">**instance_ptr**</span></span> | <span data-ttu-id="073f5-379">Pekare till objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="073f5-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="073f5-380">**klusterresursen**</span><span class="sxs-lookup"><span data-stu-id="073f5-380">**resource**</span></span> | <span data-ttu-id="073f5-381">Oanvänd parameter.</span><span class="sxs-lookup"><span data-stu-id="073f5-381">Unused parameter.</span></span> |
| <span data-ttu-id="073f5-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="073f5-382">**resource_count**</span></span> | <span data-ttu-id="073f5-383">Oanvänd parameter.</span><span class="sxs-lookup"><span data-stu-id="073f5-383">Unused parameter.</span></span> |
| <span data-ttu-id="073f5-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="073f5-384">**args_ptr**</span></span> | <span data-ttu-id="073f5-385">Oanvänd parameter.</span><span class="sxs-lookup"><span data-stu-id="073f5-385">Unused parameter.</span></span> |
| <span data-ttu-id="073f5-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="073f5-386">**args_length**</span></span> | <span data-ttu-id="073f5-387">Oanvänd parameter.</span><span class="sxs-lookup"><span data-stu-id="073f5-387">Unused parameter.</span></span> |

<span data-ttu-id="073f5-388">Vid lyckad måste objektet frisläppa objekt instans data och andra resurser som allokerats av instansen.</span><span class="sxs-lookup"><span data-stu-id="073f5-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="073f5-389">Exempel på LWM2M-klientprogram</span><span class="sxs-lookup"><span data-stu-id="073f5-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="073f5-390">Följande kod är ett exempel på ett enkelt LWM2M klient program som implementerar en anpassad enhet som består av en temperatur sensor och en ljus växel.</span><span class="sxs-lookup"><span data-stu-id="073f5-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="073f5-391">Enheten gör att en server kan läsa värdet för temperatur sensorn och den booleska statusen för ljus växeln och för att ställa in ljus växeln på/av.</span><span class="sxs-lookup"><span data-stu-id="073f5-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```