---
title: Kapitel 3 – Beskrivning Azure RTOS NetX Duo MQTT Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo MQTT-klienttjänster (anges nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cc08f7c0dceb84d5843e25384275557d2871e3546d90579aab006119a2d9980c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797525"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX Duo MQTT-klienttjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo MQTT-klienttjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nxd_mqtt_client_create Skapa** *MQTT-klientinstans*
- **nxd_mqtt_client_will_message_set** *ange will-meddelandet*
- **nxd_mqtt_client_client_login_set Ange** *användarnamn och lösenord för MQTT-klientinloggning*
- **nxd_mqtt_client_connect** *Anslut MQTT-klient till meddelandekö*
- **nxd_mqtt_client_secure_connect** *Anslut MQTT-klient till meddelandekö med TLS-säkerhet*
- **nxd_mqtt_client_publish** *Publicera ett meddelande via den autjämnare.*
- **nxd_mqtt_client_subscribe Prenumerera** *på ett ämne*
- **nxd_mqtt_client_unsubscribe Avbryta** *prenumerationen på ett ämne*
- **nxd_mqtt_client_receive_notify_set Ange** *funktionen för att ta emot MQTT-meddelanden om återanrop*
- **nxd_mqtt_client_message_get hämta** *ett meddelande från den a broker*
- **nxd_mqtt_client_disconnect_notify_set Ange** *funktionen för att koppla från MQTT-meddelande för att meddela om återanrop*
- **nxd_mqtt_client_disconnect** *MQTT-klienten från den a broker*
- **nxd_mqtt_client_delete Ta** *bort MQTT-klientinstansen*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Skapa MQTT-klientinstans

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en MQTT-klientinstans på den angivna IP-instansen. Den  client_id-strängen skickas till servern under MQTT-anslutningsfasen som *klientidentifierare (ClientId).* Den skapar också nödvändiga ThreadX-resurser (MQTT Client-uppgiftstråd, mutex, händelseflaggasgrupp och TCP-socket).

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **client_name** Klientnamnssträng.
- **client_id** Klient-ID-sträng som används under anslutningsfasen. MQTT-koordinatorn använder client_id för att unikt identifiera en klient.
- **client_id_length** Längden på klient-ID-strängen, i byte.
- **ip_ptr** Pekare till IP-instans.
- **pool_ptr** Pekare till en paketpool som MQTT-klienten använder för åtgärden.
- **stack_ptr** Stackområde för MQTT-klienttråden.
- **stack_size** Storleken på stackområdet, i byte.
- **mqtt_thread_priority** Prioriteten för MQTT-tråden.
- **memory_ptr** Deprecated. Används inte längre.
- **memory_size** Deprecated. Används inte längre.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) MQTT-klienten har skapats.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock, ip_ptr eller paketpoolspekare.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Ogiltigt ämnessträng, will_retrain_flag eller will_QoS värde.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

Anger Will-meddelandet

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>Description

Den här tjänsten anger det valfria ämnet och kommer att visas innan klienten ansluter till servern. Ämnet måste vara UTF-8-kodad sträng.

Will-meddelandet skickas, om det är inställt, till den a broker som en del av CONNECT-meddelandet. Därför måste programmet som vill använda meddelandet använda den här tjänsten innan MQTT-anslutningen upprättas.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **will_topic** UTF-8-kodad kommer att ämnessträng. Ämnet Will måste finnas. Anroparen måste se till will_topic strängen är giltig *tills nx_mqtt_client_connect* anropet görs.
- **will_topic_length** Antal byte i strängen för will-ämnet
- **will_message** Meddelande om att programmet har definierats. Om meddelandet inte krävs kan programmet ange det här fältet till *NX_NULL.*
- **will_message_length** Antal byte i meddelandesträngen will. Om will_message är inställt på NULL will_message_length måste anges till 0.
- **will_retain_flag** Om servern publicerar will-meddelandet som ett kvarhållet meddelande. Giltiga värden *är NX_TRUE* eller *NX_FALSE.*
- **will_QoS** QoS-värdet som används av servern när den skickar kommer att visas. Giltiga värden är 0 eller 1.  

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Anger will-meddelandet.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS nivå 2-meddelanden stöds inte.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Ogiltigt ämnessträng, will_retrain_flag eller will_QoS värde.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

Anger användarnamn och lösenord för MQTT-klientinloggning

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>Description

Den här tjänsten anger användarnamnet och lösenordet, som används under MQTT-anslutningsfasen för inloggning i autentiseringssyfte.

MQTT-klientinloggning med användarnamn och lösenord är valfritt. I situationer där servern kräver ett användarnamn och lösenord måste användarnamnet och lösenordet anges innan anslutningen upprättas.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **användarnamn** UTF-8-kodad användarnamnssträng. Anroparen måste hålla användarnamnssträngen giltig *tills nx_mqtt_client_connect* anropet görs.
- **username_length** Antal byte i användarnamnsträngen
- **lösenord** Lösenordssträng. Om lösenord inte krävs kan det här fältet anges till NX_NULL.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Anger will-meddelandet.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Ogiltig användarnamnssträng eller lösenordssträng.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

Anslut MQTT-klient till den a broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Description

Den här tjänsten initierar en anslutning till den a broker. Först binder den en TCP-socket och gör sedan en TCP-anslutning. Om det lyckas skapas en timer om funktionen MQTT keep alive är aktiverad. Sedan ansluter den till MQTT-servern (broker).

Observera att den här tjänsten skapar en MQTT-anslutning utan TLS-skydd. För att skapa en säker MQTT-anslutning ska programmet använda tjänsten ***nxd_mqtt_client_secure_connect().***

Om klienten vid anslutningen anger att *clean_session* ska NX_FALSE, kommer klienten att skicka om alla meddelanden som lagrats och som inte har bekräftats ännu.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **server_ip** Koordinator-IP-adress.
- **server_port** Portnummer för koordinator. Standardporten för MQTT definieras som **_NXD_MQTT_PORT_** (1883).
- **keep_alive** Keep Alive-värdet i sekunder som ska användas under sessionen. Värdet anger den maximala tiden mellan två MQTT-kontrollmeddelanden som skickas till den a broker innan den a broker uppnår sin time out för den här klienten. Värdet 0 inaktiverar funktionen keep-alive.
- **clean_session** Om servern ska starta den här sessionen eller inte. Giltiga alternativ är **_NX_TRUE_*_ eller _*_NX_FALSE._**
- **wait_option** Väntetid för anslutning.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Lyckad MQTT-anslutning
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) Klienten är redan ansluten till den a broker.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Det gick inte att hämta MQTT mutex 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) Det gick inte att ansluta till den a broker.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Det går inte att skicka meddelanden till den a broker.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server svarade med fel
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Serversvarskod
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Serversvarskod
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Serversvarskod
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Serversvarskod
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Serversvarskod
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock, ip_ptr eller paketpoolspekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

Anslut MQTT-klient till meddelandekö med TLS-säkerhet

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Description

Den här tjänsten är identisk ***med nxd_mqtt_client_connect*** förutom att anslutningen går via TLS-lagret i stället för TCP. Därför skyddas kommunikationen mellan klienten och den autjämnaren.

Den användardefinierade funktionen *tls_setup* en återanropsfunktion som MQTT-klienten använder innan en MQTT-klientanslutning upprättas. Programmet ska initiera NetX Secure TLS, konfigurera säkerhetsparametrar och läsa in relevanta certifikat som ska användas under TLS-handskakning. Den faktiska TLS-handskakningen sker när en TCP-anslutning har upprättats på den a brokerns MQTT TLS-port (standard-TCP-port 8883). När TLS-handskakningen har lyckats skickas MQTT CONNECT-kontrollpaketet via TLS.

För att kunna skapa säkra anslutningar måste NetX Secure TLS-biblioteket vara tillgängligt och NetX Duo MQTT-klienten måste byggas med ***NX_SECURE_ENABLE*** definieras.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **server_ip** Koordinator-IP-adress.
- **server_port** Portnummer för koordinator. Standardporten för MQTT definieras som **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Återanropsfunktion för konfiguration av TLS-konfiguration från användaren. Den här återanropsfunktionen anropas för att konfigurera anslutningsparametrar för TLS-klienten.
- **keep_alive** Keep-alive-värdet som ska användas under sessionen. Värdet 0 inaktiverar funktionen keep-alive.
- **clean_session** Huruvida servern ska starta den här sessionen eller inte. Giltiga alternativ är **_NX_TRUE_*_ eller _*_NX_FALSE._**
- **wait_option** Väntetid för anslutning.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Lyckad MQTT-klientanslutning upprättad via TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) Klienten är redan ansluten till den a broker.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Det gick inte att hämta MQTT mutex 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) Det gick inte att ansluta till den a broker.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Det går inte att skicka meddelanden till den a broker.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server svarade med felmeddelandet.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Serversvarskod
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Serversvarskod
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Serversvarskod
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Serversvarskod
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Serversvarskod
- NX_PTR_ERROR (0x07) Ogiltig MQTT-kontrollblock eller adressstruktur förver.
- NX_INVALID_PORT (0x46) Serverporten får inte vara 0.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Indataparameterfel
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT-tråden har inte startats ännu.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

Publicera ett meddelande via den a broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Description

Den här tjänsten publicerar ett meddelande via den a broker. Publicering av meddelanden på QoS-nivå 2 stöds inte ännu.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **topic_name** Ämne att publicera till.
- **topic_name_length** Ämnets längd i byte.
- **meddelande** Pekare till meddelandebufferten.
- **message_length** Meddelandets storlek i byte
- **behåll** Avgör om den a broker ska behålla meddelandet.
- **QoS** Önskat QoS-värde: 0 eller 1.
- **tidsgräns** Timeout-värde

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Lyckad MQTT-klient för att skapa
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Det gick inte att hämta paket från paketpoolen.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Det gick inte att kommunicera med den a broker.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS nivå 2-meddelanden stöds inte.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock, ip_ptr eller paketpoolspekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) Indataparameterfel

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

Prenumerera på ett ämne

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>Description

Den här tjänsten prenumererar på ett visst ämne. Att prenumerera på QoS nivå 2-meddelanden stöds inte ännu.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **topic_name** Ämne att publicera till.
- **topic_name_length** Ämnets längd i byte.
- **QoS Önskad QoS-nivå:** 0 eller 1.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Prenumererar på ämnet.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) Klienten är inte ansluten till den a broker.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Det gick inte att hämta MQTT mutex
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Det går inte att skicka meddelanden till den a broker.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages stöds inte.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock, ip_ptr eller paketpoolspekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name har inte angetts eller topic_name_length är noll eller QoS är ogiltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

Avbryta prenumerationen på ett ämne

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>Description

Den här tjänsten avbryter prenumerationen på ett ämne.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **topic_name** Ämne att avbryta prenumerationen på.
- **topic_name_length** Ämnets längd i byte.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Har avslutat prenumerationen på ämnet.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) Klienten är inte ansluten till den a broker.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Det gick inte att hämta MQTT mutex.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Det går inte att skicka meddelanden till den a broker.
- NX_PTR_ERROR (0x07) Ogiltig MQTT-kontrollblockspekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name har inte angetts eller topic_name_length är noll.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

Ställ in funktionen för att ta emot MQTT-meddelande om att meddela motringning

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion med MQTT-klienten. När MQTT-klienten får ett meddelande som publicerats av den a broker lagrar den meddelandet i mottagningskön. Om motringningsfunktionen har angetts anropas återanropsfunktionen för att meddela programmet att ett meddelande är redo att hämtas. Funktionen receive notify tar en pekare till MQTT-klientens kontrollblock och en *message_count* som anger antalet meddelanden som är tillgängliga i ta emot-kön. Observera att antalet kan ändras mellan mottagningsmeddelandet och när programmet hämtar dessa meddelanden, eftersom nya meddelanden kan ha anlänt i intervallet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **receive_notify** Användaren har angett återanropsfunktion som ska anropas när ett meddelande tas emot.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Konfigurera funktionen receive notify.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

Hämta ett meddelande från den a broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>Description

Den här tjänsten hämtar ett meddelande som publicerats av den a broker. Alla inkommande meddelanden lagras i mottagningskön. Programmet använder den här tjänsten för att hämta dessa meddelanden. Det här anropet är inte blockerande. Om mottagningskön är tom returnerar den här tjänsten ***NXD_MQTT_NO_MESSAGE** _. Ett program som vill meddelas om inkommande meddelanden kan anropa tjänsten _ *_nxd_mqtt_client_receive_notify_set_** för att registrera en motringningsfunktionen för mottagning.

Anroparen måste ange minnesutrymme för ämnessträngen och meddelandetexten. Storlekarna på dessa två buffertar skickas med hjälp av *topic_buffer_size* och *message_buffer_size*. Det faktiska antalet byte i ämnessträngen och meddelandetexten returneras i *actual_topic_length* och *actual_message_length*. Om ämneslängden eller längden på en längd på ett ämne är större än buffertutrymmet returnerar den här tjänsten *felkoden NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

Programmet ska allokera en större buffert och försöka igen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **topic_buffer** Pekare till den minnesplats där ämnessträngen kopieras till.
- **topic_buffer_size** Ämnesbuffertens storlek.
- **actual_topic_length** Pekare till den minnesplats där den faktiska ämneslängden returneras.
- **message_buffer** Pekare till den minnesplats där meddelandesträngen kopieras till.
- **message_buffer_size** Storleken på meddelandebufferten.
- **actual_message_length** Pekare till den minnesplats där meddelandelängden returneras.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Meddelandet har hämtats.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Internt logikfel
- **NXD_MQTT_NO_MESSAGE** (0x1000A) Mottagningskön är tom.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Ämnesbuffert eller meddelandebuffert är för liten för ämnet eller meddelandet.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock, ip_ptr eller paketpoolspekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer eller topic_buffer pekare är NULL

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

Ställ in funktionen för att koppla från MQTT-meddelande – meddela återanrop

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Description

Den här tjänsten registrerar en återanropsfunktion med MQTT-klienten. När MQTT identifierar att anslutningen till den autjämnare har gått förlorad anropas den här aviseringsfunktionen för att varna programmet. Programmet kan därför använda den här återanropsfunktionen för att identifiera en förlorad anslutning och för att kunna återupprätta anslutningen till den autjämnare.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.
- **disconnect_notify** Användaren har angett återanropsfunktionen som ska anropas när MQTT identifierar att anslutningen till den autjämnare som förloras.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Konfigurera funktionen disconnect notify.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

Koppla bort MQTT-klienten från den a broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten kopplar bort klienten från den autjämnare. Observera att meddelanden i mottagningskön släpps. Meddelanden med QoS 1 i överföringskön släpps inte. När klienten återansluter till servern kan QoS 1-meddelanden bearbetas, såvida inte klienten återansluter till servern med *clean_session-flaggan* inställd ***på NX_TRUE***.

Om anslutningen gjordes med TLS-säkerhetsskydd stänger den här tjänsten TLS-sessionen innan TCP-anslutningen kopplas från.

Det faktiska tcp socket-frånkopplingsanropet har ett väntealternativ som definieras av NXD_MQTT_SOCKET_TIMEOUT (timer tick). Standardvärdet är NX_WAIT_FOREVER. För att undvika obegränsad stängning om nätverksanslutningen går förlorad eller om servern inte svarar anger du det här alternativet till ett begränsat värde.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) Har kopplats från från koordinator
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Det gick inte att hämta MQTT mutex.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

Ta bort MQTT-klientinstansen

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort MQTT-klientinstansen och släpper interna resurser. Den här tjänsten kopplar automatiskt bort klienten från den autjämnare om den fortfarande är ansluten. Meddelanden som ännu inte har överförts eller som inte har bekräftats släpps. Meddelanden som tas emot men inte hämtas av programmet släpps också.

Om anslutningen gjordes med TLS-säkerhetsskydd stänger den här tjänsten TLS-sessionen innan TCP-anslutningen kopplas från.

När klienten har tagits bort måste ett program som vill använda MQTT-tjänsten skapa en ny instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT-klientens kontrollblock.

### <a name="return-values"></a>Returvärden

- **NXD_MQTT_SUCCESS** (0x00) MQTT-klienten har tagits bort.
- NX_PTR_ERROR (0x07) Ogiltigt MQTT-kontrollblock

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
