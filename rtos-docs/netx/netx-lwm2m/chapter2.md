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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX-LWM2M

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX LWM2M-komponenten.

## <a name="product-distribution"></a>Produkt distribution

NetX LWM2M finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Paketet innehåller tre källfiler, en inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_lwm2m_client. h**: rubrik fil för netx Lwm2m-klienten

- **nx_lwm2m_ *. c/h**: c/h källfiler för netx-lwm2m

- **demo_netx_lwm2m_client. c**: c-källfil för netx Lwm2m client demo

- **NetX_LWM2M_User_Guide.pdf**: PDF-Beskrivning av netx LWM2M-produkten

## <a name="netx-lwm2m-installation"></a>NetX LWM2M-installation

För att kunna använda NetX-LWM2M bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX är installerad. Om NetX till exempel är installerat i katalogen "*\\ ThreadX \\ ARM7 \\ grönt*" måste *nx_lwm2m&#42;. &#42;* -filer kopieras till den här katalogen.

## <a name="using-netx-lwm2m"></a>Använda NetX LWM2M

Det är enkelt att använda NetX LWM2M. I princip måste program koden innehålla *nx_lwm2m_client. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx. När *nx_lwm2m_client. h* ingår kan program koden sedan göra netx lwm2m-funktions anropen senare i den här hand boken. Programmet måste också importera *nx_lwm2m&#42;. &#42;* -filer till netx-biblioteket.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar LWM2M-klient biblioteket och programmet med LWM2M-klienten. Konfigurations alternativen kan definieras i program källan på kommando raden, om inget annat anges.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

Definierad tar bort det grundläggande LWM2M-API: et och förbättrar prestandan. API-retur koder som inte påverkas av inaktive ring av fel kontroll visas i fetstil i API-definitionen.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

Definierad, tar bort stöd för värden för flytt ALS värden. När du har inaktiverat LWM2M-klienten kan inte använda resurser med data typen float.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

Definierad, tar bort stöd för värden för 64-bitars flytt ALS värden. LWM2M-klienten kan fortfarande ta emot TLV-meddelanden som innehåller 64-bitars flytande siffror, men värdena konverteras till 32-bitars flytt punkt för bearbetning.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

Anger prioriteten för LWM2M-klientens tråd. Som standard definieras värdet som 16 för att ange prioritet 16.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

Anger det högsta antalet felkoder som lagras av enhetsobjektet. Standardvärdet är 8.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

Anger det maximala antalet säkerhets objekt instanser. Standardvärdet är 2 för att stödja en Start Server och en standard server.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

Anger det maximala antalet Server objekt instanser. Standardvärdet är 1 för att stödja en enda standard server.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

Anger den maximala längden för en server-URI, inklusive avslutande av Nil-tecken. Standardvärdet är 128.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Anger det maximala antalet Access Control instanser. Standardvärdet är 0, vilket inaktiverar åtkomst kontroll. Om programmet har stöd för mer än en LWM2M-Server, måste det maximala antalet Access Control instanser anges till det maximala antalet objekt instanser som LWM2M-klienten stöder, eftersom en Access Control instans måste skapas för varje objekt instans (utom säkerhets objekts instanserna).

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Anger det maximala antalet ACL-resurser per Access Control instans. Standardvärdet är 4.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

Anger det maximala antalet meddelanden som LWM2M-klienten har stöd för. En LWM2M-Server kan ange meddelanden om objekt, objekt instanser och resurser. Standardvärdet är 8.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

Anger det maximala antalet resurser per objekt. Standardvärdet är 32.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

Anger den längsta vänte tiden för bootstrap-server begär anden när bootstrap-sessionen initieras innan sessionen avbryts. Standardvärdet är 60 sekunder.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

Anger den maximala vänte tiden för slut för ande av DTLS-handskakning. Standardvärdet är 30 sekunder.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

Anger den maximala vänte tiden för slut för ande av DTLS. Standardvärdet är 5 sekunder.
