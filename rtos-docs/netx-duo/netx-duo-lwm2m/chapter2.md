---
title: Kapitel 2 – installation och användning av återställnings tider NetX Duo LWM2M-klienten
description: I det här kapitlet beskrivs hur du installerar och använder återställnings tider NetX Duo LWM2M-klienten.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 536225de30f54356157c222917fc904c6aa039fe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825950"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>Kapitel 2 installation och användning av LWM2M-klienten

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av LWM2M-klient komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider LWM2M-klienten kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/) . Paketet innehåller tre källfiler, en inkludera filer, enligt följande.

* **NX \_ lwm2m \_ client. h** -huvudfilen för lwm2m-klienten

* **NX \_ lwm2m \_ client. c** c källfiler för lwm2m-klient

* **demo \_ netx \_ lwm2m \_ client. c** c-källfil för lwm2m client demo

## <a name="lwm2m-client-installation"></a>LWM2M-klient installation

LWM2M-klienten är en del av NetX Duo. Efter kloning av NetX duo från GitHub-lagringsplatsen kan du därför hitta LWM2M klient källa på ***netxduo/addons/LWM2M***.

## <a name="using-lwm2m_client"></a>Använda LWM2M- \_ klient

Det är enkelt att använda LWM2M-klienten. Program koden måste i princip innehålla en ***NX \_ lwm2m \_ -klient. h ** _ efter att det innehåller _*_TX \_ API. h_*_ och _*_NX \_ API. h_*_, för att använda ThreadX och netx. När _*_NX \_ lwm2m \_ client. h_*_ ingår, kan program koden sedan göra lwm2m klient funktions anrop senare i den här hand boken. Programmet måste också importera _* _nx lwm2m- \_ \_ klienten \_ . \**** Files till netx-biblioteket.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar LWM2M-klient biblioteket och programmet med LWM2M-klienten. Konfigurations alternativen kan definieras i program källan på kommando raden, om inget annat anges.

| Konfigurations &nbsp; alternativ | Beskrivning |
| --- | --- |
| **NX \_ LWM2M- \_ klientens \_ MTU** | Anger den maximala storleken för ett CoAP-meddelande, inklusive IP-och UDP-huvuden. Standardvärdet är 1280. |
| **NX \_ LWM2M \_ client \_ socket \_ TOS** | Typ av tjänst som krävs för LwM2M-UDP. Som standard definieras det här värdet som NX \_ IP \_ Normal för att ange en normal IP-paketfiltrering. |
| **NX \_ LWM2M \_ client \_ socket \_ TTL** | Anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80. |
| **NX \_ LWM2M- \_ klientens \_ socket- \_ kö \_ Max** | Anger antalet maximala djup i mottagnings kön. Standardvärdet är inställt på 4. |
| **NX \_ LWM2M- \_ klient \_ Max COAP-URI- \_ \_ \_ sökväg** | Anger antalet Max längder för alternativet CoAP Uri-Path. Standardvärdet är inställt på 32. |
| **NX \_ LWM2M \_ klient \_ Max \_ enhets \_ fel** | Anger det högsta antalet felkoder som lagras av enhetsobjektet. Standardvärdet är 8. |
| **NX \_ LWM2M- \_ klient \_ Max \_ säkerhets \_ instanser** | Anger det maximala antalet säkerhets objekt instanser. Standardvärdet är 2 för att stödja en Start Server och en standard server. |
| **NX \_ LWM2M- \_ klient \_ Max \_ Server \_ instanser** | Anger det maximala antalet Server objekt instanser. Standardvärdet är 1 för att stödja en enda standard server. |
| **NX \_ LWM2M \_ - \_ klient \_ Max \_ instanser för åtkomst kontroll \_** | Anger det maximala antalet Access Control instanser. Standardvärdet är 0, vilket inaktiverar åtkomst kontroll. Om programmet har stöd för mer än en LWM2M-Server, måste det maximala antalet Access Control instanser anges till det maximala antalet objekt instanser som LWM2M-klienten stöder, eftersom en Access Control instans måste skapas för varje objekt instans (utom säkerhets objekts instanserna). |
| **NX \_ LWM2M- \_ klient \_ Max \_ åtkomst \_ kontrol \_ listor för åtkomst kontroll** | Anger det maximala antalet ACL-resurser per Access Control instans. Standardvärdet är 4. |
| **NX \_ LWM2M \_ klient \_ Max \_ meddelanden** | Anger det maximala antalet meddelanden som LWM2M-klienten har stöd för. En LWM2M-Server kan ange meddelanden om objekt, objekt instanser och resurser. Standardvärdet är 8. |
| **NX \_ LWM2M- \_ klient \_ Max \_ resurser** | Anger det maximala antalet resurser per objekt. Standardvärdet är 32. |
| **NX \_ LWM2M- \_ klient \_ Max \_ flera \_ resurser** | Anger det maximala antalet resurs instanser för flera resurser. Standardvärdet är 8. |
| **NX \_ LWM2M- \_ klient \_ Start timer för \_ inaktivitet \_** | Anger den längsta vänte tiden för bootstrap-server begär anden när bootstrap-sessionen initieras innan sessionen avbryts. Standardvärdet är 60 sekunder. |
| **NX \_ LWM2M \_ client \_ DTLS \_ Start \_ timeout** | Anger den maximala vänte tiden för slut för ande av DTLS-handskakning. Standardvärdet är 30 sekunder. |
| **NX \_ LWM2M \_ klient \_ DTLS \_ slut \_ tids gräns** | Anger den maximala vänte tiden för slut för ande av DTLS. Standardvärdet är 5 sekunder. |
| **NX \_ LWM2M \_ klient \_ säkerhet \_ Max \_ Server- \_ URI** | Anger den maximala längden för en server-URI, inklusive avslutande NULL-tecken. Standardvärdet är 128. |
| **NX \_ LWM2M \_ klient \_ säkerhet \_ Max \_ offentlig \_ nyckel \_ eller \_ identitet** | Anger den maximala längden för den offentliga nyckeln eller identiteten för DTLS. Standardvärdet är 128. |
| **NX \_ LWM2M \_ klient \_ säkerhet \_ Max \_ Server \_ offentlig \_ nyckel** | Anger den maximala längden för serverns offentliga nyckel för DTLS. Standardvärdet är 128. |
| **NX \_ LWM2M \_ klient \_ säkerhet \_ Max \_ hemlig \_ nyckel** | Anger den maximala längden för den hemliga nyckeln för DTLS. Standardvärdet är 128. |
| **NX \_ LWM2M- \_ klienten håller på att \_ stoppas \_** | Anger hur många sekunder som ska förflyta innan start programmet initieras. Standardvärdet är 1 sekund. |
| **NX \_ LWM2M- \_ klientens \_ livs längd \_** | Anger antalet sekunder för registrerings livs längden. Standardvärdet är 600 sekunder. |
