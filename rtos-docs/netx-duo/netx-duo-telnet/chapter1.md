---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo Telnet
description: Azure återställnings tider NetX Duo Telnet är ett protokoll som har utformats för att överföra kommandon och svar mellan två noder på Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d25f5ca4a7bf1ecf4c3d0c68ef6c8aeda7800098
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825734"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo Telnet

Azure återställnings tider NetX Duo Telnet är ett protokoll som har utformats för att överföra kommandon och svar mellan två noder på Internet. Telnet är ett enkelt protokoll som använder Reliable Transmission Control Protocol (TCP)-tjänster för att utföra sin överförings funktion. Därför är Telnet ett mycket tillförlitligt överförings protokoll. Telnet är också ett av de mest använda program protokollen.

## <a name="telnet-requirements"></a>Telnet-krav

För att kunna fungera korrekt kräver Telnet-paketet NetX Duo att en NetX-IP-instans redan har skapats. Dessutom måste TCP vara aktiverat på samma IP-instans. Telnet-klient delen av NetX Duo Telnet-paketet har inga ytterligare krav.

Telnet-Server delen av NetX Duo Telnet-paketet har ett ytterligare krav. Den kräver fullständig åtkomst till TCP *-välkända port 23* för hantering av alla Telnet-begäranden i klienten.

## <a name="telnet-constraints"></a>Telnet-begränsningar 

NetX Duo Telnet-protokollet implementerar Telnet-standarden. Tolkningen och svaret på Telnet-kommandon som anges av en byte med värdet 255, är dock programmets ansvar. De olika Telnet-kommandona och kommando parametrarna definieras i *nxd_telnet_client. h-och nxd_telnet_server. h* -filer.

## <a name="telnet-communication"></a>Telnet-kommunikation

Som tidigare nämnts använder Telnet-servern den *välkända TCP-porten 23* för att fält klient begär Anden. Telnet-klienter kan använda alla tillgängliga TCP-portar.

## <a name="telnet-authentication"></a>Telnet-autentisering

Telnet-autentisering är ansvaret för programmets motringnings funktion för Telnet-servern. Motringningen till programmets Telnet-Server "ny anslutning" skulle normalt fråga klienten om namn och/eller lösen ord. Klienten ansvarar då för att tillhandahålla informationen. Servern bearbetar sedan informationen i återanropet "Receive data". Det är här som program Server koden skulle behöva autentisera informationen och avgöra om den är giltig eller inte.

## <a name="telnet-new-connection-callback"></a>Telnet, ny motringning för anslutning

NetX Duo Telnet-servern anropar den programspecifika återanrops funktionen när en ny begäran om Telnet-klienten tas emot. Programmet anger återanrops funktionen när Telnet-servern skapas via funktionen ***nx_telnet_server_create*** . Vanliga åtgärder för återanropet "ny anslutning" inkluderar att skicka en banderoll eller en prompt till klienten. Detta kan mycket bra innehålla en prompt för inloggnings information.

### <a name="prototype"></a>Prototyp

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot den anropande Telnet-servern.
- **logical_connection**: den interna logiska anslutningen för Telnet-servern. Detta kan användas av programmet som ett index i buffertar och/eller data strukturer som är specifika för varje klient anslutning. Värdet sträcker sig från 0 till NX_TELNET_MAX_CLIENTS-1.

## <a name="telnet-receive-data-callback"></a>Motringning från Telnet-data

NetX Duo Telnet-servern anropar den programspecificerade motringningsfunktionen varje gång som en ny Telnet-klient data tas emot. Programmet anger återanrops funktionen när Telnet-servern skapas via funktionen ***nx_telnet_server_create*** . Vanliga åtgärder för motringning till "ny anslutning" är att lägga till eko data och/eller parsa data och tillhandahålla data som ett resultat av att ett kommando från klienten tolkas.

Observera att den här återkallnings rutinen även måste släppa det angivna paketet.

### <a name="prototype"></a>Prototyp

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>Indataparametrar

- **server_ptr**: pekar mot den anropande Telnet-servern.
- **logical_connection**: den interna logiska anslutningen för Telnet-servern. Detta kan användas av programmet som ett index i buffertar och/eller data strukturer som är specifika för varje klient anslutning. Värdet sträcker sig från 0 till NX_TELNET_MAX_CLIENTS-1.
- **packet_ptr**: pekar mot paket som innehåller data från klienten.

## <a name="telnet-end-connection-callback"></a>Återanrop för Telnet-avsluta anslutning

NetX Duo Telnet-servern anropar den programspecificerade callback-funktionen när en Telnet-klient avslutar anslutningen. Programmet anger återanrops funktionen när Telnet-servern skapas via funktionen ***nx_telnet_server_create*** . Vanliga åtgärder för återanropet "Avsluta anslutning" är bland annat rensning av alla klient särskilda data strukturer som är associerade med den logiska anslutningen.

### <a name="prototype"></a>Prototyp
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till den anropande Telnet-servern.
- **logical_connection** Den interna logiska anslutningen för Telnet-servern. Detta kan användas av programmet som ett index i buffertar och/eller data strukturer som är specifika för varje klient anslutning. Värdet sträcker sig från 0 till NX_TELNET_MAX_CLIENTS-1.

## <a name="telnet-option-negotiation"></a>Alternativ förhandling för Telnet

NetX Duo Telnet-servern har stöd för en begränsad uppsättning Telnet-alternativ, ECHO och förhindras gå vidare.

Om du vill aktivera den här funktionen får NX_TELNET_SERVER_OPTION_DISABLE inte definieras. Som standard är den inte definierad. Telnet-servern skapar en adresspool i *nx_telnet_server_create* tjänst som den allokerar paket för att skicka Telnet-alternativ till klienten. Se "konfigurations alternativ" för att ange paketets nytto Last (NX_TELNET_SERVER_PACKET_PAYLOAD) och storlek för Packet pool (NX_TELNET_SERVER_PACKET_POOL_SIZE) för den här poolen. Den här poolen tas bort när *nx_telnet_server_deletes* tjänsten anropas.

När du upprättar en anslutning till Telnet-klienten kommer den att skicka ut den här uppsättningen Telnet-alternativ till klienten om den inte har fått alternativ begär Anden från klienten:

- kommer eko
- eko inte
- kommer att SGA

När Telnet-data tas emot från klienten, kontrollerar Telnet-servern om den första byten är "IAC"-koden. I så fall kommer de att bearbeta alla alternativ i klient paketet. Alternativ som inte finns i listan ovan ignoreras.

Som standard skapar Telnet-servern sin egen interna adresspool om NX_TELNET_SERVER_OPTION_DISABLE inte har definierats och den måste överföra Telnet-alternativ. Programpoolen för Telnet Server definieras av NX_TELNET_SERVER_PACKET_PAYLOAD och NX_TELNET_SERVER_PACKET_POOLSIZE. Men om NX_TELNET_SERVER_USER_CREATE_PACKET_POOL har definierats måste programmet skapa paket poolen för Telnet-servern och ange den som en Programpakets-pool för Telnet genom att anropa *_nx_telnet_server_packet_pool_set*. Mer information om den här funktionen finns i kapitel 3 "Beskrivning av Telnet-tjänster".

Till skillnad från NetX Duo Telnet-servern skickar och svarar inte NetX Duo Telnet-klientens uppgifts tråd automatiskt och svarar på mottagna alternativ från Telnet-servern. Detta måste göras av Telnets klient program.

## <a name="telnet-multi-thread-support"></a>Stöd för Telnet multi-Thread

NetX Duo Telnet Client Services kan anropas från flera trådar samtidigt. Läs-eller Skriv förfrågningar för en viss Telnet-serverinstans bör dock göras i följd från samma tråd.

## <a name="telnet-rfcs"></a>Telnet-rapporter

NetX Duo Telnet är kompatibel med RFC854 och relaterade RFC: er.
