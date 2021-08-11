---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo MQTT
description: NetX Duo MQTT-klientpaketet kräver att NetX Duo (version 5.10 eller senare) installeras, är korrekt konfigurerad och att IP-instansen har skapats.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be650186b233d0f1202beecc22f4bd8bc0af4dbe0f677704d09df057fcbc34fc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797746"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo MQTT

## <a name="netx-duo-mqtt-requirements"></a>Krav för NetX Duo MQTT

För Azure RTOS NetX Duo MQTT-klientpaketet krävs att NetX Duo (version 5.10 eller senare) installeras, är korrekt konfigurerad och att IP-instansen har skapats. TCP-modulen måste vara aktiverad i systemet. Om TLS-säkerhet krävs måste dessutom NetX Secure TLS-modulen konfigureras enligt den säkerhetsparameter som krävs av den a broker.

## <a name="netx-duo-mqtt-specification"></a>NetX Duo MQTT-specifikation

NetX Duo MQTT client implement är kompatibel med OASIS MQTT version 3.1.1<sup>29</sup> okt 2014. Specifikationen finns på:

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>Grundläggande åtgärd för NetX Duo MQTT

MQTT (Message Queue Telemetry Transport) baseras på modellen utgivare-prenumerant. En klient kan publicera information till andra klienter via en a broker. En klient, om du är intresserad av ett ämne, kan prenumerera på ämnet via den a broker. En a broker ansvarar för att leverera publicerade meddelanden till sina klienter som prenumererar på ämnet. I den här modellen för utgivare och prenumerant kan flera klienter publicera data med samma ämne. En klient får ett meddelande som publiceras om klienten prenumererar på samma ämne.

Beroende på användningsfallet kan en klient välja någon av de tre QoS-nivåerna när ett meddelande publiceras:

- **QoS 0:** Meddelandet levereras högst en gång. Meddelanden som skickas med QoS 0 kan gå förlorade.
- **QoS 1:** Meddelandet levereras minst en gång. Meddelanden som skickas med QoS 1 kan levereras mer än en gång.
- **QoS 2:** Meddelandet levereras exakt en gång. Meddelanden som skickas med QoS 2 levereras garanterat utan duplicering.

> [!NOTE]
> Den här implementeringen av MQTT-klienten stöder inte meddelanden på QoS-nivå 2.

Eftersom QoS 1 och QoS 2 garanterat levereras håller koordinatorn reda på tillståndet för QoS 1- och QoS 2-meddelanden som skickas till varje klient. Detta är särskilt viktigt för klienter som förväntar sig QoS1- eller QoS 2-meddelanden. Klienten kan kopplas bort från den a broker (till exempel när klienten startas om eller kommunikationslänken tillfälligt går förlorad). Koordinatorn måste lagra QoS 1- och QoS 2-meddelanden så att meddelandena kan levereras senare när klienten återansluts till den a broker. Klienten kan dock välja att inte ta emot inaktuella meddelanden från den a broker efter återanslutningen. Klienten kan göra det genom att initiera anslutningen med *clean_session* inställd på ***NX_TRUE** _. I det här fallet ska koordinatorn, när den tar emot MQTT CONNECT-meddelandet, ta bort all sessionsinformation som är associerad med klienten, inklusive meddelanden om QoS 1 eller QoS 2 som inte har levererades eller som inte har bekräftats. Om _clean_session*-flaggan_ är till * NX_FALSE , ska servern skicka QoS 1- och QoS 2-meddelandena igen. MQTT-klienten skickar även om eventuella obekräftelser om _clean_session* är inställt på ***NX_TRUE*.** Den här bekräftelsen skiljer sig från TCP-lagretSCK, även om det också sker. MQTT-klienten skickar en bekräftelse till koordinatorn.

Ett program skapar en MQTT-klientinstans genom att anropa ***nxd_mqtt_client_create()** _. När klienten har skapats kan programmet ansluta till den a broker genom att anropa _*_nxd_mqtt_client_connect()_*_. När du har anslutit till den a broker kan klienten prenumerera på ett ämne genom att anropa _*_nxd_mqtt_client_subscribe()_*_ eller publicera ett ämne genom att anropa _*_nxd_mqtt_client_publish()_**.

Inkommande MQTT-meddelanden lagras i mottagningskön i MQTT-klientinstansen. Programmet hämtar dessa meddelanden genom att anropa ***nxd_mqtt_client_message_get()***. Om det finns meddelanden i mottagningskön returneras det första meddelandet (t.ex. det äldsta) från kön till anroparen. Ämnessträngen från meddelandet returneras också.

> [!NOTE]
> Funktionen ***nxd_mqtt_client_message_get()** _ blockerar inte om MQTT-klientens mottagningskö är tom. Funktionen returnerar omedelbart med returkoden _*_NXD_MQTT_NO_MESSAGE_**. Programmet ska behandla det här returvärdet som en indikation på att mottagningskön är tom, inte ett fel.

För att undvika att avssöka kön för inkommande meddelanden kan programmet registrera en återanropsfunktion med MQTT-klienten genom att ***anropa nxd_mqtt_client_recieve_notify_set()***. Återanropsfunktionen deklareras som:

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

När MQTT-klienten tar emot meddelanden från den a broker anropar den återanropsfunktionen om funktionen har angetts. Motringningsfunktionen skickar pekaren till klientkontrollblocket och ett värde för antal meddelanden. Värdet för antal meddelanden anger antalet MQTT-meddelanden i mottagningskön. Observera att den här återanropsfunktionen körs i MQTT-klienttrådkontexten. Därför bör återanropsfunktionen inte köra några procedurer som kan blockera MQTT-klienttråden. Motringningsfunktionen ska utlösa programtråden för att ***anropa nxd_mqtt_client_message_get()*** för att hämta meddelanden.

För att koppla från och avsluta MQTT-klienttjänsten ska programmet använda tjänsten ***nxd_mqtt_client_disconnect()** _ _*_och nxd_mqtt_client_delete()._*_ När _*_nxd_mqtt_client_disconnect() anropas kopplar_*_ du helt enkelt från TCP-anslutningen till den autjämnare. Den släpper meddelanden som redan tagits emot och lagrats i mottagningskön. Den släpper dock inte QoS nivå 1-meddelanden i överföringskön. Meddelanden på QoS-nivå 1 skickas igen vid _*_anslutningen, förutsatt att clean_session-flaggan_*_ är inställd på _ *_NX_FALSE._**

Den a broker kan också koppla från klienten. När TCP-anslutningen mellan klienten och den a broker avslutas kan programmet meddelas via aviseringsfunktionen koppla från. Om du vill använda meddelandemekanismen installerar programmet funktionen disconnect notify genom att anropa ***nxd_mqtt_client_disconnect_notify_set*.** När en TCP-frånkoppling observeras och MQTT-sessionen har skapats anropas meddelandefunktionen.

När ***nxd_mqtt_client_delete()*** anropas frigörs alla meddelandeblock i överföringskön och mottagningskön. Meddelanden på QoS-nivå 1 som inte är kända tas också bort.

## <a name="secure-mqtt-connection"></a>Säker MQTT-anslutning

MQTT-klienten upprättar en säker anslutning till koordinatorn med hjälp av NetX Secure TLS-modulen. Standardportnumret för MQTT med TLS-säkerhet är 8883, som definieras ***i NXD_MQTT_TLS_PORT***.

För att skapa en säker MQTT-anslutning till koordinatorn måste en TLS-session förhandlas efter att en TCP-anslutning har upprättats innan MQTT CONNECT-meddelanden kan skickas till den a broker. TLS-sessionen som konfigureras sker genom att ***anropa nxd_mqtt_client_secure_connect()*** och skicka in en användardefinierad återanropsfunktion för TLS-konfiguration. Under MQTT-anslutningsfasen, när TCP-anslutningen har upprättats, anropar klienten återanropsfunktionen för TLS-installation för att starta en korrekt TLS-handskakningsprocess. När TLS-sessionen har upprättats fortsätter klienten MQTT CONNECT-meddelandet via den säkra kanalen.

Den användardefinierade återanropsfunktionen tar fem indatavärden och deklareras som:

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

Nedan visas en beskrivning av indataparametrarna:

- **client_ptr:** Pekare till MQTT-klientkontrollblocket.
- **session_ptr:** Pekare till TLS-sessionskontrollblocket.
- **certificate_ptr:** Pekare till certifikatkontrollblocket. Konfigurationsfunktionen konfigurerar det här certifikatet innan det skickas till koordinatorn.
- **trusted_certificate_ptr:** Pekare till det betrodda certifikatet. TLS-konfigurationsfunktionen konfigurerar det betrodda certifikatet för att autentisera servern.

I TLS-konfigurationsfunktionen ansvarar programmet för att skapa en TLS-session och konfigurera sessionen med ett korrekt certifikat. Följande pseudokod beskriver en typisk startprocedur för TLS-session. Läsaren refereras till NetX Secure TLS-användarhandboken för information om hur du använder TLS-API:er.

Nedan visas ett exempel på ett återanrop för TLS-konfiguration:

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

- NetX Duo MQTT stöder inte sändning eller mottagning av QoS nivå 2-meddelanden.
- NetX Duo MQTT stöder inte kedjepaket.
