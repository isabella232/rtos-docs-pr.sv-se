---
title: Bilaga D – Azure återställnings tider NetX BSD-Compatible socket API
description: 'Lär dig mer om API: et för BSD-Compatible socket för IPv4.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9062e27d8f447ac8d36e7a09afee5ac14f86f8c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826898"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>Bilaga D – Azure återställnings tider NetX BSD-Compatible socket API

## <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible socket

API-anrop för BSD-Compatible socket har stöd för en delmängd av BSD-API-anrop (med vissa begränsningar) genom att använda Azure återställnings tider NetX-primitiver under. IPv4-protokoll och nätverks adresser stöds. Detta API-skikt i BSD-Compatible Sockets ska fungera lika snabb eller något snabbare än vanliga BSD-implementeringar eftersom detta API använder interna NetX-primitiver och kringgår onödig fel kontroll av NetX.

Med konfigurerbara alternativ kan värd programmet definiera maximalt antal Sockets, maximal storlek för TCP-fönster och djup i lyssnings kön.

På grund av prestanda-och arkitektur begränsningar stöder detta BSD-Compatible Sockets-API: t inte alla BSD-anrop i BSD. Dessutom är inte alla BSD-alternativ tillgängliga för BSD-tjänsterna, särskilt följande:

- Funktionen ***Select** _ fungerar med endast _fd_set \* readfds *, andra argument i det här anropet, t. ex. *writefds*, *exceptfds* stöds inte.
- Argumentet *för int-flaggor* stöds inte för funktionerna ***send** _, _*_Recv_*_, _*_SendTo_*_ och _ *_recvfrom_**. API: et för BSD-Compatible socket stöder endast en begränsad uppsättning BSD Sockets-anrop.

Käll koden är utformad för enkelhet och består endast av två filer, ***nx_bsd. c** _ och _*_nx_bsd. h_*_. Installationen kräver att du lägger till de här två filerna i build-projektet (inte NetX-biblioteket) och skapar värd programmet som ska använda BSD socket service-anrop. Filen _ *_nx_bsd. h_** måste också ingå i program källan. Exempel på demonstrations filer ingår i distributionen som är gratis tillgänglig med NetX. Mer information finns i hjälpen BSD-Compatible socket API **417** och readme filer som är sammankopplade med API-paketet BSD-Compatible socket.

API: erna för BSD-Compatible Sockets stöder följande API-anrop i BSD:

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
