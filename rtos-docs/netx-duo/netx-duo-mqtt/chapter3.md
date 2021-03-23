---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo MQTT Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo MQTT-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825896"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo MQTT Client Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo MQTT client-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nxd_mqtt_client_create** *skapa en MQTT-klient instans*
- **nxd_mqtt_client_will_message_set** *ställer in meddelandet*
- **nxd_mqtt_client_client_login_set** *Ange MQTT användar namn och lösen ord för klient inloggning*
- **nxd_mqtt_client_connect** *ansluta MQTT-klienten till Service Broker*
- **nxd_mqtt_client_secure_connect** *ansluta MQTT-klienten till KOORDINATORn med TLS-säkerhet*
- **nxd_mqtt_client_publish** *publicera ett meddelande via Broker.*
- **nxd_mqtt_client_subscribe** *Prenumerera på ett ämne*
- **nxd_mqtt_client_unsubscribe** *avbryta prenumerationen på ett ämne*
- **nxd_mqtt_client_receive_notify_set** *Ange MQTT meddelande ta emot meddelande om motringning*
- **nxd_mqtt_client_message_get** *Hämta ett meddelande från Service Broker*
- **nxd_mqtt_client_disconnect_notify_set** *Ange MQTT meddelande om att koppla från* meddelande om motringning
- **nxd_mqtt_client_disconnect** *från koppling av MQTT-klienten från Broker*
- **nxd_mqtt_client_delete** *ta bort MQTT-klient instansen*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Skapa MQTT-klient instans

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en MQTT-klient instans på den angivna IP-instansen. *Client_id* strängen skickas till servern under MQTT-anslutnings fasen som *klient-ID (ClientId)*. Det skapar också de nödvändiga ThreadX-resurserna (MQTT klient aktivitets tråd, mutex, händelse flagg grupp och TCP-socket).

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **client_name** Klient namn sträng.
- **client_id** Klient-ID-sträng som används under anslutnings fasen. MQTT-Broker använder den här client_id för att unikt identifiera en klient.
- **client_id_length** Längden på klient-ID-strängen, i byte.
- **ip_ptr** Pekare till IP-instans.
- **pool_ptr** Pekare till en Packet Pools MQTT-klient använder för att utföra åtgärden.
- **stack_ptr** Stack Area för MQTT-klientens tråd.
- **stack_size** Storlek på stackområdet, i byte.
- **mqtt_thread_priority** Prioriteten för MQTT-tråden.
- **memory_ptr** Föråldrad. Används inte längre.
- **memory_size** Föråldrad. Används inte längre.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har skapat MQTT-klienten.
- Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block, ip_ptr eller Packet pool-pekare.
- NXD_MQTT_INVALID_PARAMETER (0x10009) ogiltig kommer att sträng, will_retrain_flag eller will_QoS värde.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Anger att meddelandet ska visas

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

### <a name="description"></a>Beskrivning

Den här tjänsten anger det valfria avsnittet och meddelandet skickas innan klienten ansluter till servern. Avsnittet måste vara UTF-8-kodad sträng.

Om det är inställt skickas meddelandet till Service Broker som en del av ANSLUTNINGS meddelandet. Programmet som ska användas måste därför använda den här tjänsten innan MQTT-anslutningen görs.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **will_topic** UTF-8-kodad ämnes sträng. Ämnet måste finnas. Anroparen måste ha will_topic strängen giltig till *nx_mqtt_client_connect* anropet görs.
- **will_topic_length** Antal byte i ämnes strängen
- **will_message** Det program som definierats kommer att visas. Om meddelandet inte är obligatoriskt kan programmet ange det här fältet som *NX_NULL.*
- **will_message_length** Antal byte i meddelande strängen som ska skickas. Om will_message är inställt på NULL måste will_message_length anges till 0.
- **will_retain_flag** Anger om servern ska publicera meddelandet som ett kvarhållet meddelande. Giltiga värden är *NX_TRUE* eller *NX_FALSE.*
- **will_QoS** QoS-värdet som används av servern när meddelandet skickas visas. Giltiga värden är 0 och 1.  

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0x00) anger att meddelandet ska visas.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) QoS-nivå 2-meddelanden stöds inte.
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.
- NXD_MQTT_INVALID_PARAMETER (0x10009) ogiltig kommer att sträng, will_retrain_flag eller will_QoS värde.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Anger MQTT användar namn och lösen ord för klient inloggning

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger användar namn och lösen ord, som används vid MQTT anslutnings fasen för inloggning i autentisering.

MQTT-klientens inloggning med användar namn och lösen ord är valfritt. I situationer där servern kräver ett användar namn och lösen ord måste användar namnet och lösen ordet anges innan anslutningen upprättas.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **användar namn** UTF-8-kodad användar namn sträng. Anroparen måste ha användar namn strängen giltig till *nx_mqtt_client_connect* anropet görs.
- **username_length** Antal byte i användar namn strängen
- **lösen ord** Lösen ords sträng. Om lösen ord inte krävs kan det här fältet anges till NX_NULL.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0x00) anger att meddelandet ska visas.
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.
- NXD_MQTT_INVALID_PARAMETER (0x10009) ogiltig användar namn sträng eller lösen ords sträng.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Anslut MQTT-klienten till Broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en anslutning till Broker. Först binder en TCP-socket och gör sedan en TCP-anslutning. Förutsatt att det lyckas skapas en timer om MQTT Keep Alive-funktionen är aktive rad. Sedan ansluter den till MQTT-servern (Broker).

Observera att den här tjänsten skapar en MQTT-anslutning utan TLS-skydd. Om du vill skapa en säker MQTT-anslutning ska programmet använda tjänsten ***nxd_mqtt_client_secure_connect ().***

Vid anslutningen, om klienten anger *clean_session* till NX_FALSE, kommer klienten att skicka om meddelanden som lagras som inte har bekräftats ännu.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **server_ip** IP-adress för Broker.
- **SERVER_PORT** Port nummer för Broker. Standard porten för MQTT definieras som **_NXD_MQTT_PORT_** (1883).
- **KEEP_ALIVE** Värdet för Keep Alive, i sekunder, som ska användas under sessionen. Värdet anger den maximala tiden mellan två MQTT som skickas till koordinatorn innan Service Broker har nått sin tids gräns för klienten. Värdet 0 stänger av Keep-Alive-funktionen.
- **clean_session** Om servern ska starta den här sessionen rensa. Giltiga alternativ är **_NX_TRUE_*_ eller _*_NX_FALSE._**
- **wait_option** Vänte tid för anslutning.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) lyckad MQTT-anslutning
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) klienten är redan ansluten till Service Broker.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX 
- Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) Det gick inte att ansluta till Broker.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** -servern (0x10008) svarade med fel
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0X10081) Server svars kod
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0X10082) Server svars kod
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0X10083) Server svars kod
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0X10084) Server svars kod
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0X10085) Server svars kod
- NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Anslut MQTT-klienten till Service Broker med TLS-säkerhet

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

### <a name="description"></a>Beskrivning

Den här tjänsten är identisk med ***nxd_mqtt_client_connect*** förutom att anslutningen går via TLS-skiktet i stället för TCP. Därför skyddas kommunikationen mellan klienten och Service Broker.

Den användardefinierade *tls_setup* är en callback-funktion som MQTT-klienten använder innan en MQTT-klient anslutning görs. Programmet ska initiera NetX Secure TLS, konfigurera säkerhets parametrar och läsa in relevanta certifikat som ska användas under TLS-handskakning. Den faktiska TLS-handskakningen inträffar efter att en TCP-anslutning har upprättats för Broker: s MQTT TLS-port (standard TCP-port 8883). När TLS-handskakningen har lyckats skickas MQTT CONNECT Control-paketet via TLS.

För att säkra anslutningar måste NetX Secure TLS-biblioteket vara tillgängligt och NetX Duo MQTT-klienten måste ha skapats med ***NX_SECURE_ENABLE*** definierat.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **server_ip** IP-adress för Broker.
- **SERVER_PORT** Port nummer för Broker. Standard porten för MQTT isdefined som **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Funktion för motringning av användar angiven TLS-installation. Denna callback-funktion anropas för att konfigurera anslutnings parametrar för TLS-klienten.
- **KEEP_ALIVE** Det Keep-Alive-värde som ska användas under sessionen. Värdet 0 stänger av Keep-Alive-funktionen.
- **clean_session** Om servern ska starta den här sessionen rensa. Giltiga alternativ är **_NX_TRUE_*_ eller _*_NX_FALSE._**
- **wait_option** Vänte tid för anslutning.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) lyckad MQTT-klient anslutning upprättad via TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) klienten är redan ansluten till Service Broker.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX 
- Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) Det gick inte att ansluta till Broker.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** -servern (0x10008) svarade med fel meddelande.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0X10081) Server svars kod
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0X10082) Server svars kod
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0X10083) Server svars kod
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0X10084) Server svars kod
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0X10085) Server svars kod
- NX_PTR_ERROR (0x07) ogiltigt MQTT-kontroll block eller server struktur.
- NX_INVALID_PORTs server port (0x46) kan inte vara 0.
- Fel i indataparametern NXD_MQTT_INVALID_PARAMETER (0x10009)
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT tråden har inte startats än.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Publicera ett meddelande via Service Broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Beskrivning

Den här tjänsten publicerar ett meddelande via Broker. Publicering av QoS-nivå 2-meddelanden stöds inte ännu.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **topic_name** Ämne att publicera till.
- **topic_name_length** Längden på ämnet i byte.
- **meddelande** Pekar på meddelande bufferten.
- **message_length** Meddelandets storlek i byte
- **Behåll** Bestämmer om Broker ska behålla meddelandet.
- **QoS** Önskat QoS-värde: 0 eller 1.
- **tids gräns** Tids gräns värde

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) lyckad MQTT-klient skapa
- **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0X10006) Det gick inte att hämta paket från mediepoolen.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att kommunicera med Broker.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) QoS-nivå 2-meddelanden stöds inte.
- NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare
- Fel i indataparametern NXD_MQTT_INVALID_PARAMETER (0x10009)

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten prenumererar på ett speciellt ämne. Det finns inte stöd för att prenumerera på QoS-nivå 2-meddelanden ännu.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **topic_name** Ämne att publicera till.
- **topic_name_length** Längden på ämnet i byte.
- **QoS den önskade QoS-nivån:** 0 eller 1.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har prenumererat på avsnittet.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) klienten är inte ansluten till Service Broker.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX
- Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) 2Messages för QoS-nivå stöds inte.
- NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name har inte angetts, eller topic_name_length är noll eller så är QoS-värdet ogiltigt.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten avbryter prenumerationen på ett ämne.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **topic_name** För att avbryta prenumerationen på.
- **topic_name_length** Längden på ämnet i byte.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har avbrutit prenumerationen från ämnet.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) klienten är inte ansluten till Service Broker.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX.
- Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) Det gick inte att skicka meddelanden till Broker.
- NX_PTR_ERROR (0x07) ogiltig MQTT Control Block-pekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name har inte angetts eller topic_name_length är noll.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ställ in MQTT Message Receive motringning funktion

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en callback-funktion med MQTT-klienten. När du tar emot ett meddelande som publicerats av Broker, lagrar MQTT-klienten meddelandet i mottagnings kön. Om motringningsfunktionen är inställt anropas funktionen motringning för att meddela programmet att ett meddelande är klart att hämtas. Funktionen Receive notify tar en pekare till klient kontroll blocket MQTT och ett *message_count* som anger antalet meddelanden som är tillgängliga i mottagnings kön. Observera att antalet kan ändras mellan mottagnings meddelandet och när programmet hämtar dessa meddelanden, eftersom nya meddelanden kan ha anlänt i intervallet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **receive_notify** Användaren har angett återanrops funktion som ska anropas vid mottagning av ett meddelande.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har angett funktionen Receive notify.
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hämta ett meddelande från Service Broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar ett meddelande som publicerats av Broker. Alla inkommande meddelanden lagras i mottagnings kön. Programmet använder den här tjänsten för att hämta dessa meddelanden. Anropet är inte blockerande. Om mottagnings kön är tom returnerar den här tjänsten ***NXD_MQTT_NO_MESSAGE** _. Ett program som vill meddelas om inkommande meddelande kan anropa tjänsten _ *_nxd_mqtt_client_receive_notify_set_** för att registrera en Receive callback-funktion.

Anroparen måste tillhandahålla minnes utrymme för ämnes strängen och meddelande texten. Storlekarna på de här två buffertarna skickas med hjälp av *topic_buffer_size* och *message_buffer_size*. Det faktiska antalet byte i ämnes strängen och meddelande texten returneras i *actual_topic_length* och *actual_message_length*. Om ämnes längden eller massage längden är större än det angivna buffertutrymme returnerar den här tjänsten felkoden *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

Programmet ska allokera en större buffert och försöka igen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **topic_buffer** Pekar på den minnes plats där ämnes strängen kopieras till.
- **topic_buffer_size** Storlek på ämnes bufferten.
- **actual_topic_length** Pekar till den minnes plats där den faktiska ämnes längden returneras.
- **message_buffer** Pekar på den minnes plats där meddelande strängen kopieras till.
- **message_buffer_size** Storlek på meddelande bufferten.
- **actual_message_length** Pekar till den minnes plats där meddelande längden returneras.

### <a name="return-values"></a>Retur värden

- Ett meddelande har hämtats **NXD_MQTT_SUCCESS** (0x00).
- Internt **NXD_MQTT_INTERNAL_ERROR** (0X10004) internt logiskt fel
- **NXD_MQTT_NO_MESSAGE** (0x1000A) mottagnings kön är tom.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D), delbufferten eller meddelande bufferten är för liten för ämnet eller meddelandet.
- NX_PTR_ERROR (0x07) ogiltigt MQTT kontroll block, ip_ptr eller Packet pool pekare
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer eller topic_buffer pekare är NULL

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ange MQTT Message koppla från meddela motringning funktion

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar en callback-funktion med MQTT-klienten. När MQTT upptäcker att anslutningen till Broker förloras, anropas den här meddelande funktionen för att varna programmet. Programmet kan därför använda denna callback-funktion för att identifiera en förlorad anslutning och för att kunna återupprätta anslutningen till koordinatorn igen.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.
- **disconnect_notify** Användaren har angett callback-funktionen som ska anropas när MQTT identifierar anslutningen till Broker förloras.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har ställt in funktionen för att koppla från meddelande.
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Koppla från MQTT-klienten från Broker

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar från klienten från Broker. Observera att meddelanden i mottagnings kön släpps. Meddelanden med QoS 1 i överförings kön släpps inte. När klienten återansluter till servern kan QoS 1-meddelanden bearbetas, såvida inte klienten återansluter till servern med *clean_session* flagga inställd på ***NX_TRUE***.

Om anslutningen har gjorts med TLS-säkerhetsskydd stänger den här tjänsten TLS-sessionen innan du kopplar från TCP-anslutningen.

Det faktiska anropet från TCP-socketen har ett vänte alternativ som definieras av NXD_MQTT_SOCKET_TIMEOUT (timer Tick). Standardvärdet är NX_WAIT_FOREVER. För att undvika obestämd avstängning i händelse av att nätverks anslutningen tappas bort eller servern inte svarar anger du det här alternativet till ett ändligt värde.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har frånkopplats från Broker
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) Det gick inte att hämta MQTT MUTEX.
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

Ta bort klient instansen MQTT

### <a name="prototype"></a>Prototyp

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort MQTT-klient instansen och frigör interna resurser. Den här tjänsten kopplar automatiskt bort klienten från Service Broker om den fortfarande är ansluten. Meddelanden som inte har skickats eller som inte har godkänts har frigjorts. Meddelanden som mottagits men inte hämtats av programmet släpps också.

Om anslutningen gjordes med TLS-säkerhetsskydd stänger den här tjänsten TLS-sessionen innan du kopplar bort TCP-anslutningen.

När klienten har tagits bort måste ett program som vill använda MQTT-tjänsten skapa en ny instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till MQTT klient kontroll block.

### <a name="return-values"></a>Retur värden

- **NXD_MQTT_SUCCESS** (0X00) har tagit bort MQTT-klienten.
- NX_PTR_ERROR (0x07) ogiltigt MQTT Control Block

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
