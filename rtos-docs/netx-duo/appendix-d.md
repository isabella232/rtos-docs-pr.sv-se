---
title: Bilaga D – Azure återställnings tider NetX Duo BSD-Compatible socket API
description: 'Lär dig mer om API: et för BSD-Compatible socket för IPv4 och IPv6.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82439184d9facb6ddcc08ce81bc51182d7f34429
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826232"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Bilaga D – Azure återställnings tider NetX Duo BSD-Compatible socket API

## <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible socket 
API-anrop för BSD-Compatible socket har stöd för en delmängd av BSD-API-anrop (med vissa begränsningar) genom att använda NetX Duo- &reg; primitiver under. Både IPv6-och IPv4-protokoll och nätverks adresser stöds. Detta API-skikt i BSD-Compatible Sockets ska fungera lika snabb eller något snabbare än vanliga BSD-implementeringar eftersom detta API använder interna NetX Duo-primitiver och kringgår onödig fel kontroll av NetX.  

Med konfigurerbara alternativ kan värd programmet definiera maximalt antal Sockets, maximal storlek för TCP-fönster och djup i lyssnings kön.

På grund av prestanda-och arkitektur begränsningar stöder detta BSD-Compatible Sockets-API: t inte alla BSD-anrop i BSD. Dessutom är inte alla BSD-alternativ tillgängliga för BSD-tjänsterna, särskilt följande:

  - ***Välj** _ anrop fungerar med endast fd_set \_ readfds, andra argument i det här anropet, t. ex. writefds, exceptfds stöds inte.
  - Argumentet "int Flags" stöds inte för ***send** _-, _*_Recv_*_-, _*_SendTo-_*_ och _ *_recvfrom_**-anrop. 
  - API: et för BSD-Compatible socket stöder endast en begränsad uppsättning BSD Sockets-anrop.

Käll koden är utformad för enkelhet och består endast av två filer, ***nxd_bsd. c** _ och _*_nxd_bsd. h_*_. Installationen kräver att du lägger till de här två filerna i build-projektet (inte NetX-biblioteket) och skapar värd programmet som ska använda BSD socket service-anrop. Filen _ *_nxd_bsd. h_** måste också ingå i program källan. Exempel på demonstrations filer för både IPv4-och IPv6-baserade program ingår i distributionen som är tillgänglig fritt med NetX Duo. Mer information finns i hjälp-och README-filerna som paketeras med BSDCompatible socket-API-paketet.

API: erna för BSD-Compatible Sockets stöder följande API-anrop i BSD:

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```