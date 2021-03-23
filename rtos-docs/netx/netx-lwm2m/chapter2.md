---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX-LWM2M
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX LWM2M-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826700"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="ee27c-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX-LWM2M</span><span class="sxs-lookup"><span data-stu-id="ee27c-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="ee27c-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX LWM2M-komponenten.</span><span class="sxs-lookup"><span data-stu-id="ee27c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="ee27c-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="ee27c-105">Product Distribution</span></span>

<span data-ttu-id="ee27c-106">NetX LWM2M finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="ee27c-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="ee27c-107">Paketet innehåller tre källfiler, en inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ee27c-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="ee27c-108">**nx_lwm2m_client. h**: rubrik fil för netx Lwm2m-klienten</span><span class="sxs-lookup"><span data-stu-id="ee27c-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="ee27c-109">\*\*nx_lwm2m_ \*. c/h\*\*: c/h källfiler för netx-lwm2m</span><span class="sxs-lookup"><span data-stu-id="ee27c-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="ee27c-110">**demo_netx_lwm2m_client. c**: c-källfil för netx Lwm2m client demo</span><span class="sxs-lookup"><span data-stu-id="ee27c-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="ee27c-111">**NetX_LWM2M_User_Guide.pdf**: PDF-Beskrivning av netx LWM2M-produkten</span><span class="sxs-lookup"><span data-stu-id="ee27c-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="ee27c-112">NetX LWM2M-installation</span><span class="sxs-lookup"><span data-stu-id="ee27c-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="ee27c-113">För att kunna använda NetX-LWM2M bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerad.</span><span class="sxs-lookup"><span data-stu-id="ee27c-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="ee27c-114">Om NetX till exempel är installerat i katalogen "*\\ ThreadX \\ ARM7 \\ grönt*" måste *nx_lwm2m&#42;. &#42;* -filer kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="ee27c-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="ee27c-115">Använda NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="ee27c-115">Using NetX LWM2M</span></span>

<span data-ttu-id="ee27c-116">Det är enkelt att använda NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="ee27c-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="ee27c-117">I princip måste program koden innehålla *nx_lwm2m_client. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx.</span><span class="sxs-lookup"><span data-stu-id="ee27c-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="ee27c-118">När *nx_lwm2m_client. h* ingår kan program koden sedan göra netx lwm2m-funktions anropen senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="ee27c-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="ee27c-119">Programmet måste också importera *nx_lwm2m&#42;. &#42;* -filer till netx-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="ee27c-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="ee27c-120">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="ee27c-120">Configuration Options</span></span>

<span data-ttu-id="ee27c-121">Det finns flera konfigurations alternativ när du skapar LWM2M-klient biblioteket och programmet med LWM2M-klienten.</span><span class="sxs-lookup"><span data-stu-id="ee27c-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="ee27c-122">Konfigurations alternativen kan definieras i program källan på kommando raden, om inget annat anges.</span><span class="sxs-lookup"><span data-stu-id="ee27c-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="ee27c-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="ee27c-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="ee27c-124">Definierad tar bort det grundläggande LWM2M-API: et och förbättrar prestandan.</span><span class="sxs-lookup"><span data-stu-id="ee27c-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="ee27c-125">API-retur koder som inte påverkas av inaktive ring av fel kontroll visas i fetstil i API-definitionen.</span><span class="sxs-lookup"><span data-stu-id="ee27c-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="ee27c-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="ee27c-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="ee27c-127">Definierad, tar bort stöd för värden för flytt ALS värden.</span><span class="sxs-lookup"><span data-stu-id="ee27c-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="ee27c-128">När du har inaktiverat LWM2M-klienten kan inte använda resurser med data typen float.</span><span class="sxs-lookup"><span data-stu-id="ee27c-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="ee27c-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="ee27c-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="ee27c-130">Definierad, tar bort stöd för värden för 64-bitars flytt ALS värden.</span><span class="sxs-lookup"><span data-stu-id="ee27c-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="ee27c-131">LWM2M-klienten kan fortfarande ta emot TLV-meddelanden som innehåller 64-bitars flytande siffror, men värdena konverteras till 32-bitars flytt punkt för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="ee27c-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="ee27c-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="ee27c-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="ee27c-133">Anger prioriteten för LWM2M-klientens tråd.</span><span class="sxs-lookup"><span data-stu-id="ee27c-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="ee27c-134">Som standard definieras värdet som 16 för att ange prioritet 16.</span><span class="sxs-lookup"><span data-stu-id="ee27c-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="ee27c-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="ee27c-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="ee27c-136">Anger det högsta antalet felkoder som lagras av enhetsobjektet.</span><span class="sxs-lookup"><span data-stu-id="ee27c-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="ee27c-137">Standardvärdet är 8.</span><span class="sxs-lookup"><span data-stu-id="ee27c-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="ee27c-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="ee27c-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="ee27c-139">Anger det maximala antalet säkerhets objekt instanser.</span><span class="sxs-lookup"><span data-stu-id="ee27c-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="ee27c-140">Standardvärdet är 2 för att stödja en Start Server och en standard server.</span><span class="sxs-lookup"><span data-stu-id="ee27c-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="ee27c-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="ee27c-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="ee27c-142">Anger det maximala antalet Server objekt instanser.</span><span class="sxs-lookup"><span data-stu-id="ee27c-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="ee27c-143">Standardvärdet är 1 för att stödja en enda standard server.</span><span class="sxs-lookup"><span data-stu-id="ee27c-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="ee27c-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="ee27c-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="ee27c-145">Anger den maximala längden för en server-URI, inklusive avslutande av Nil-tecken.</span><span class="sxs-lookup"><span data-stu-id="ee27c-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="ee27c-146">Standardvärdet är 128.</span><span class="sxs-lookup"><span data-stu-id="ee27c-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="ee27c-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="ee27c-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="ee27c-148">Anger det maximala antalet Access Control instanser.</span><span class="sxs-lookup"><span data-stu-id="ee27c-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="ee27c-149">Standardvärdet är 0, vilket inaktiverar åtkomst kontroll.</span><span class="sxs-lookup"><span data-stu-id="ee27c-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="ee27c-150">Om programmet har stöd för mer än en LWM2M-Server, måste det maximala antalet Access Control instanser anges till det maximala antalet objekt instanser som LWM2M-klienten stöder, eftersom en Access Control instans måste skapas för varje objekt instans (utom säkerhets objekts instanserna).</span><span class="sxs-lookup"><span data-stu-id="ee27c-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="ee27c-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="ee27c-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="ee27c-152">Anger det maximala antalet ACL-resurser per Access Control instans.</span><span class="sxs-lookup"><span data-stu-id="ee27c-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="ee27c-153">Standardvärdet är 4.</span><span class="sxs-lookup"><span data-stu-id="ee27c-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="ee27c-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="ee27c-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="ee27c-155">Anger det maximala antalet meddelanden som LWM2M-klienten har stöd för.</span><span class="sxs-lookup"><span data-stu-id="ee27c-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="ee27c-156">En LWM2M-Server kan ange meddelanden om objekt, objekt instanser och resurser.</span><span class="sxs-lookup"><span data-stu-id="ee27c-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="ee27c-157">Standardvärdet är 8.</span><span class="sxs-lookup"><span data-stu-id="ee27c-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="ee27c-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="ee27c-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="ee27c-159">Anger det maximala antalet resurser per objekt.</span><span class="sxs-lookup"><span data-stu-id="ee27c-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="ee27c-160">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="ee27c-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="ee27c-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="ee27c-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="ee27c-162">Anger den längsta vänte tiden för bootstrap-server begär anden när bootstrap-sessionen initieras innan sessionen avbryts.</span><span class="sxs-lookup"><span data-stu-id="ee27c-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="ee27c-163">Standardvärdet är 60 sekunder.</span><span class="sxs-lookup"><span data-stu-id="ee27c-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="ee27c-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ee27c-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="ee27c-165">Anger den maximala vänte tiden för slut för ande av DTLS-handskakning.</span><span class="sxs-lookup"><span data-stu-id="ee27c-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="ee27c-166">Standardvärdet är 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="ee27c-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="ee27c-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ee27c-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="ee27c-168">Anger den maximala vänte tiden för slut för ande av DTLS.</span><span class="sxs-lookup"><span data-stu-id="ee27c-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="ee27c-169">Standardvärdet är 5 sekunder.</span><span class="sxs-lookup"><span data-stu-id="ee27c-169">The default value is 5 seconds.</span></span>
