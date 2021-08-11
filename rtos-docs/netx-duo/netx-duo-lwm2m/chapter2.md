---
title: Kapitel 2 – Installation och användning av RTOS NetX Duo LWM2M-klienten
description: I det här kapitlet beskrivs hur du installerar och använder RTOS NetX Duo LWM2M-klienten.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f804ae59dd639ca05d1b8f5251cf8b878e78bb9ad2575e08c21d43b14e727a19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796522"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>Kapitel 2 Installation och användning av LWM2M-klienten

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av LWM2M-klientkomponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS LWM2M Client kan hämtas från vår offentliga källkodsdatabas på [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/) . Paketet innehåller tre källfiler, en med filer, enligt följande.

* **nx \_ lwm2m \_ client.h-huvudfil** för LWM2M-klienten

* **nx \_ lwm2m \_ client.c** C Källfiler för LWM2M Client

* **demo \_ netx \_ lwm2m \_ client.c** C Källfil för LWM2M Client Demo

## <a name="lwm2m-client-installation"></a>LWM2M-klientinstallation

LWM2M-klienten är en del av NetX Duo. Efter kloningen av NetX Duo från GitHub-lagringsplatsen finns därför LWM2M-klientkällan på ***netxduo/addons/lwm2m***.

## <a name="using-lwm2m_client"></a>Använda LWM2M-klienten \_

Det är enkelt att använda LWM2M-klienten. I princip måste programkoden innehålla ***nx \_ lwm2m client.h* _ efter att den innehåller \_ *_*_tx \_ api.h_ _ och *_*_nx \_ api.h_ _, för att kunna använda *ThreadX och NetX. När _*_nx \_ lwm2m \_ client.h_ _ ingår kan programkoden sedan göra *de LWM2M Client-funktionsanrop som anges senare i den här guiden. Programmet måste också importera filen _* _nx \_ lwm2m \_ client \_ . \**** till NetX-biblioteket.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar LWM2M-klientbiblioteket och programmet med hjälp av LWM2M-klienten. Konfigurationsalternativen kan definieras i programkällan på kommandoraden, om inget annat anges.

| &nbsp;Konfigurationsalternativ | Description |
| --- | --- |
| **NX \_ LWM2M \_ CLIENT \_ MTU** | Anger den maximala storleken för ett CoAP-meddelande, inklusive IP- och UDP-huvuden. Standardvärdet är 1280. |
| **NX \_ LWM2M \_ KLIENT SOCKET \_ \_ TOS** | Typ av tjänst som krävs för LwM2M UDP. Som standard definieras det här värdet som NX \_ IP NORMAL för att indikera normal \_ IP-pakettjänst. |
| **NX \_ LWM2M \_ CLIENT \_ SOCKET \_ TTL** | Anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80. |
| **MAXIMALT \_ ANTAL NX LWM2M-KLIENTSOCKETKÖER \_ \_ \_ \_** | Anger antalet maximala djup för mottagningskön. Standardvärdet är inställt på 4. |
| **NX \_ LWM2M \_ CLIENT \_ MAX \_ COAP \_ URI \_ PATH** | Anger antalet maximala längder för alternativet CoAP-Uri-Path. Standardvärdet är inställt på 32. |
| **NX \_ LWM2M-KLIENTENS \_ \_ \_ \_ MAXENHETSFEL** | Anger det maximala antalet felkoder som lagras av enhetsobjektet. Standardvärdet är 8. |
| **NX \_ LWM2M \_ CLIENT \_ MAX \_ SECURITY \_ INSTANCES** | Anger det maximala antalet Security Object Instances. Standardvärdet är 2 för att stödja en Bootstrap-server och en standardserver. |
| **NX \_ LWM2M \_ CLIENT \_ MAX \_ SERVER \_ INSTANCES** | Anger det maximala antalet serverobjektinstanser. Standardvärdet är 1 för att stödja en enskild standardserver. |
| **INSTANSER FÖR MAXIMAL ÅTKOMSTKONTROLL FÖR NX \_ LWM2M-KLIENT \_ \_ \_ \_ \_** | Anger det maximala antalet Access Control instanser. Standardvärdet är 0, vilket inaktiverar åtkomstkontroll. Om programmet stöder fler än en LWM2M-server måste det maximala antalet Access Control-instanser anges till det maximala antalet objektinstanser som LWM2M-klienten stöder, eftersom en Access Control-instans måste skapas för varje objektinstans (förutom säkerhetsobjektinstanserna). |
| **\_ÅTKOMSTKONTROLL-ACL:ER FÖR NX LWM2M-KLIENTEN \_ \_ \_ \_ \_** | Anger det maximala antalet ACL-resurser per Access Control instans. Standardvärdet är 4. |
| **MEDDELANDEN OM \_ MAXIMALT ANTAL NX LWM2M-KLIENTER \_ \_ \_** | Anger det maximala antalet meddelanden som LWM2M-klienten stöder. En LWM2M-server kan ange meddelanden för objekt, objektinstanser och resurser. Standardvärdet är 8. |
| **NX \_ LWM2M \_ CLIENT \_ MAX \_ RESOURCES** | Anger det maximala antalet resurser per objekt. Standardvärdet är 32. |
| **NX \_ LWM2M-KLIENTEN \_ MAX FLERA \_ \_ \_ RESURSER** | Anger det maximala antalet resursinstanser för flera resurser. Standardvärdet är 8. |
| **NX \_ LWM2M KLIENTEN \_ \_ BOOTSTRAP \_ IDLE \_ TIMER** | Anger den maximala väntetiden för bootstrap-serverbegäranden när bootstrap-sessionen initieras innan sessionen avbryts. Standardvärdet är 60 sekunder. |
| **NX \_ LWM2M \_ CLIENT \_ DTLS \_ \_ START-TIMEOUT** | Anger den maximala väntetiden för slutförande av DTLS-handskakning. Standardvärdet är 30 sekunder. |
| **NX \_ LWM2M-KLIENTENS \_ \_ DTLS-SLUTTIDS \_ \_ TIDSGRÄNS** | Anger den maximala tiden för att vänta på att DTLS-avstängningen ska slutföras. Standardvärdet är 5 sekunder. |
| **NX \_ LWM2M \_ \_ KLIENTSÄKERHET \_ MAX \_ \_ SERVER-URI** | Anger den maximala längden för en server-URI, inklusive avslutande null-tecken. Standardvärdet är 128. |
| **NX \_ LWM2M \_ \_ KLIENTSÄKERHET \_ MAX OFFENTLIG NYCKEL ELLER \_ \_ \_ \_ IDENTITET** | Anger den maximala längden på den offentliga nyckeln eller identiteten för DTLS. Standardvärdet är 128. |
| **NX \_ LWM2M \_ CLIENT \_ SECURITY \_ MAX \_ SERVER \_ PUBLIC \_ KEY** | Anger den maximala längden på den offentliga servernyckeln för DTLS. Standardvärdet är 128. |
| **NX \_ LWM2M \_ CLIENT \_ SECURITY \_ MAX \_ SECRET \_ KEY** | Anger den maximala längden på den hemliga nyckeln för DTLS. Standardvärdet är 128. |
| **NX \_ LWM2M \_ CLIENT \_ HOLD \_ OFF** | Anger antalet sekunder som ska vänta innan bootstrap initieras. Standardvärdet är 1 sekund. |
| **NX \_ LWM2M-KLIENTENS \_ \_ \_ LIVSLÄNGD** | Anger antalet sekunder för registreringens livslängd. Standardvärdet är 600 sekunder. |
