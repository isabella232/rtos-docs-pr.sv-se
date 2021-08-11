---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX LWM2M
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX LWM2M-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ad8963c342e907201074559929f3a7a2d70c9f13e135cd95c9a2e9b224e17cf
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791235"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX LWM2M

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX LWM2M-komponenten.

## <a name="product-distribution"></a>Produktdistribution

NetX LWM2M finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Paketet innehåller tre källfiler, en innehåller filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_lwm2m_client.h:** Huvudfil för NetX LWM2M-klienten

- **nx_lwm2m_*.c/h:** C/H-källfiler för NetX LWM2M

- **demo_netx_lwm2m_client.c:** C-källfil för NetX LWM2M Client Demo

- **NetX_LWM2M_User_Guide.pdf:** PDF-beskrivning av NetX LWM2M-produkt

## <a name="netx-lwm2m-installation"></a>NetX LWM2M-installation

För att kunna använda NetX LWM2M ska hela distributionen som nämns ovan kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen "*\\ threadx \\ arm7 \\ green*" ska *nx_lwm2m&#42;.&#42;* kopieras till den här katalogen.

## <a name="using-netx-lwm2m"></a>Använda NetX LWM2M

Det är enkelt att använda NetX LWM2M. I princip måste programkoden innehålla *nx_lwm2m_client.h* efter att den *innehåller tx_api.h* *och nx_api.h*, för att kunna använda ThreadX och NetX. När *nx_lwm2m_client.h* ingår kan programkoden sedan göra de NetX LWM2M-funktionsanrop som anges senare i den här guiden. Programmet måste också importera *nx_lwm2m&#42;.&#42;* till NetX-biblioteket.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar LWM2M-klientbiblioteket och programmet med hjälp av LWM2M-klienten. Konfigurationsalternativen kan definieras i programkällan på kommandoraden, om inget annat anges.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

Definierad tar bort det grundläggande API:et för LWM2M-klientfelkontroll och förbättrar prestandan. API-returkoder som inte påverkas av inaktivering av felkontroll visas i fetstil i API-definitionen.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

Definierad tar bort stödet för flyttalsvärden. När den är inaktiverad kan LWM2M-klienten inte stödja resurser med flyttalsdatatypen.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

Definierad tar bort stödet för 64-bitars flyttalsnummervärden. LWM2M-klienten kan fortfarande ta emot TLV-meddelanden som innehåller 64-bitars flyttal, men värdena konverteras till 32-bitars flyttal för bearbetning.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

Anger prioriteten för LWM2M-klienttråden. Som standard definieras det här värdet som 16 för att ange prioritet 16.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

Anger det maximala antalet felkoder som lagras av enhetsobjektet. Standardvärdet är 8.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

Anger det maximala antalet Security Object Instances. Standardvärdet är 2 för att stödja en Bootstrap-server och en standardserver.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

Anger det maximala antalet serverobjektinstanser. Standardvärdet är 1 för att stödja en enskild standardserver.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

Anger den maximala längden för en server-URI, inklusive avslutande nil tecken. Standardvärdet är 128.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Anger det maximala antalet Access Control instanser. Standardvärdet är 0, vilket inaktiverar åtkomstkontroll. Om programmet stöder fler än en LWM2M-server måste det maximala antalet Access Control-instanser anges till det maximala antalet objektinstanser som LWM2M-klienten stöder, eftersom en Access Control-instans måste skapas för varje objektinstans (förutom säkerhetsobjektinstanserna).

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Anger det maximala antalet ACL-resurser per Access Control instans. Standardvärdet är 4.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

Anger det maximala antalet meddelanden som LWM2M-klienten stöder. En LWM2M-server kan ange meddelanden för objekt, objektinstanser och resurser. Standardvärdet är 8.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

Anger det maximala antalet resurser per objekt. Standardvärdet är 32.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

Anger den maximala väntetiden för bootstrap-serverbegäranden när bootstrap-sessionen initieras innan sessionen avbryts. Standardvärdet är 60 sekunder.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

Anger den maximala väntetiden för slutförande av DTLS-handskakning. Standardvärdet är 30 sekunder.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

Anger den maximala tiden för att vänta på att DTLS-avstängningen ska slutföras. Standardvärdet är 5 sekunder.
