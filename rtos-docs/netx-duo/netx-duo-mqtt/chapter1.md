---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo MQTT
description: Klient paketet NetX Duo MQTT kräver att NetX Duo (version 5,10 eller senare) installeras, är korrekt konfigurerat och att IP-instansen har skapats.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825911"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo MQTT

## <a name="netx-duo-mqtt-requirements"></a>NetX Duo MQTT-krav

Azure återställnings tider NetX Duo MQTT client-paketet kräver att NetX Duo (version 5,10 eller senare) installeras, är korrekt konfigurerat och att IP-instansen har skapats. TCP-modulen måste vara aktive rad i systemet. Om TLS-säkerhet krävs måste dessutom NetX Secure TLS-modulen konfigureras enligt den säkerhets parameter som krävs av Service Broker.

## <a name="netx-duo-mqtt-specification"></a>NetX Duo MQTT-specifikation

NetX Duo MQTT client IMPLEMENT är kompatibel med OASIS MQTT version 3.1.1, oktober<sup>2014.</sup> Du hittar specifikationen på:

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>NetX Duo MQTT Basic-åtgärd

MQTT (Message Queue-transport för telemetri) baseras på utgivarens prenumerations modell. En klient kan publicera information till andra klienter via en Broker. En klient, om det är intresse rad av ett ämne, kan prenumerera på avsnittet via koordinatorn. En Service Broker ansvarar för att leverera publicerade meddelanden till sina klienter som prenumererar på ämnet. I den här utgivarens prenumerations modell kan flera klienter publicera data med samma ämne. En klient får ett meddelande som publiceras om klienten prenumererar på samma ämne.

Beroende på användnings fallet kan en klient välja en av de tre QoS-nivåerna vid publicering av ett meddelande:

- **QoS 0**: meddelandet levereras högst en gång. Meddelanden som skickas med QoS 0 kan gå förlorade.
- **QoS 1**: meddelandet levereras minst en gång. Meddelanden som skickas med QoS 1 kan levereras mer än en gång.
- **QoS 2**: meddelandet levereras exakt en gång. Meddelanden som skickas med QoS 2 garanteras att levereras, utan duplicering.

> [!NOTE]
> Den här implementeringen av MQTT-klienten har inte stöd för meddelanden på QoS-nivå 2.

Eftersom QoS 1 och QoS 2 är garanterat att levereras, håller Service Broker reda på status för QoS 1-och QoS 2-meddelanden som skickas till varje klient. Detta är särskilt viktigt för klienter som förväntar sig QoS1 eller QoS 2-meddelanden. Klienten kan vara frånkopplad från koordinatorn (till exempel när klienten startas om eller om kommunikations länken är tillfälligt förlorad). Service Broker måste lagra QoS 1-och QoS 2-meddelanden så att meddelandena kan levereras senare när klienten återansluts till Broker. Klienten kan dock välja att inte ta emot inaktuella meddelanden från koordinatorn efter åter anslutning. Klienten kan göra detta genom att initiera anslutningen med flaggan *clean_session* inställd på ***NX_TRUE** _. I det här fallet, vid mottagandet av MQTT CONNECT-meddelandet, ignoreras all sessionsinformation som är associerad med den här klienten, inklusive levererade eller obekräftade QoS 1-eller QoS 2-meddelanden. Om _clean_session *-flaggan är till ***NX_FALSE**_, ska servern skicka om QoS 1-och QoS 2-meddelanden. MQTT-klienten skickar också alla meddelanden som inte har godkänts om _clean_session * är inställt på ***NX_TRUE *.** Den här bekräftelsen skiljer sig från TCP-lagrets ACK, även om det även sker. MQTT-klienten skickar en bekräftelse till Broker.

Ett program skapar en MQTT-klient instans genom att anropa ***nxd_mqtt_client_create ()** _. När klienten har skapats kan programmet ansluta till Service Broker genom att anropa _*_nxd_mqtt_client_connect ()_*_. Efter att ha anslutit till Broker kan klienten prenumerera på ett ämne genom att anropa _*_nxd_mqtt_client_subscribe ()_*_ eller publicera ett ämne genom att anropa _ *_nxd_mqtt_client_publish ()_* *.

Inkommande MQTT-meddelanden lagras i Receive-kön i MQTT-klient instansen. Programmet hämtar detta meddelande genom att anropa ***nxd_mqtt_client_message_get ()***. Om det finns meddelanden i mottagnings kön, returneras det första meddelandet (t. ex. äldsta) från kön till anroparen. Avsnitts strängen från meddelandet returneras också.

> [!NOTE]
> Funktionen ***nxd_mqtt_client_message_get ()** _ blockeras inte om MQTT-klientens mottagande kö är tom. Funktionen returnerar omedelbart med retur koden _ *_NXD_MQTT_NO_MESSAGE_* *. Programmet ska behandla detta retur värde som en indikation på att mottagnings kön är tom, inte ett fel.

För att undvika att avsöka mottagnings kön för inkommande meddelanden kan programmet registrera en callback-funktion med MQTT-klienten genom att anropa ***nxd_mqtt_client_recieve_notify_set ()***. Callback-funktionen deklareras som:

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

När MQTT-klienten tar emot meddelanden från Broker anropas funktionen motringning om funktionen har angetts. Funktionen motringning skickar pekaren till klient kontroll blocket och ett antal meddelande värden. Värdet för antal meddelanden anger antalet MQTT-meddelanden i mottagnings kön. Observera att den här funktionen för motringning körs i MQTT klient tråd kontext. Därför bör callback-funktionen inte köra några procedurer som kan blockera MQTT-klient tråden. Motringningsfunktionen ska utlösa program tråden för anrop ***nxd_mqtt_client_message_get ()*** för att hämta meddelandena.

För att koppla från och avsluta MQTT-klient tjänsten, måste programmet använda tjänsten ***nxd_mqtt_client_disconnect ()** _ och _*_nxd_mqtt_client_delete ()._*_ Anrop av _*_nxd_mqtt_client_disconnect ()_*_ kopplar bara från TCP-anslutningen till Broker. Den frigör meddelanden som redan har tagits emot och lagrats i mottagnings kön. Den släpper dock inte QoS-nivå 1-meddelanden i överförings kön. Meddelanden på QoS-nivå 1 överförs vid anslutning, förutsatt att flaggan _*_clean_session_*_ har angetts till _ *_NX_FALSE._**

Service Broker kan också koppla från klienten. När TCP-anslutningen mellan klienten och utjämningen avbryts, kan programmet meddelas av funktionen från kopplings meddelande. Om du vill använda meddelande mekanismen installerar programmet funktionen för att koppla från meddelande genom att anropa ***nxd_mqtt_client_disconnect_notify_set *.** När en TCP-från koppling observeras och MQTT-sessionen har skapats, anropas Notification-funktionen.

Anrop av ***nxd_mqtt_client_delete ()*** släpper alla meddelande block i överförings kön och mottagnings kön. Ej godkända QoS-nivå 1-meddelanden tas också bort.

## <a name="secure-mqtt-connection"></a>Säker MQTT-anslutning

MQTT-klienten skapar en säker anslutning till Broker med hjälp av NetX Secure TLS-modulen. Standard port numret för MQTT med TLS-säkerhet är 8883, definierat i ***NXD_MQTT_TLS_PORT***.

För att skapa en säker MQTT-anslutning till Broker måste en TLS-session förhandlas efter att en TCP-anslutning har upprättats, innan MQTT CONNECT-meddelanden kan skickas till Broker. TLS-sessionen har kon figurer ATS genom att anropa ***nxd_mqtt_client_secure_connect ()*** och skicka en användardefinierad funktion för MOTRINGNING av TLS-installation. När TCP-anslutningen har upprättats anropar klienten den TLS-MQTT som krävs för att starta en fungerande TLS-handskaknings process. När TLS-sessionen har upprättats fortsätter klienten MQTT CONNECT-meddelandet över den säkra kanalen.

Den användardefinierade motringningsfunktionen tar fem indatavärden och deklareras som:

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

Nedan visas en beskrivning av indataparametrarna:

- **client_ptr**: pekar på klient kontroll blocket MQTT.
- **session_ptr**: pekar mot kontroll block för TLS-session.
- **certificate_ptr**: pekar mot certifikat kontroll blocket. Installations funktionen konfigurerar det här certifikatet innan det skickas till Broker.
- **trusted_certificate_ptr**: pekar på det betrodda certifikatet. Funktionen TLS-installation konfigurerar det betrodda certifikatet för att autentisera servern.

I funktionen TLS-installation ansvarar programmet för att skapa en TLS-session och konfigurera sessionen med ett korrekt certifikat. Följande pseudo-kod visar en typisk start procedur för TLS-sessioner. Läsaren hänvisas till användar handboken för NetX Secure TLS för information om hur du använder TLS-API: er.

Nedan visas ett exempel på ett TLS-installations anrop:

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a>Kända begränsningar för NetX Duo MQTT-klienten

- NetX Duo-MQTT stöder inte sändning eller mottagning av QoS-nivå 2-meddelanden.
- NetX Duo-MQTT har inte stöd för kedjade paket.
