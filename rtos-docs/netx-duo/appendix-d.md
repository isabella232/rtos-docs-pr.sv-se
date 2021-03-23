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
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a><span data-ttu-id="09a45-103">Bilaga D – Azure återställnings tider NetX Duo BSD-Compatible socket API</span><span class="sxs-lookup"><span data-stu-id="09a45-103">Appendix D - Azure RTOS NetX Duo BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="09a45-104">API för BSD-Compatible socket</span><span class="sxs-lookup"><span data-stu-id="09a45-104">BSD-Compatible Socket API</span></span> 
<span data-ttu-id="09a45-105">API-anrop för BSD-Compatible socket har stöd för en delmängd av BSD-API-anrop (med vissa begränsningar) genom att använda NetX Duo- &reg; primitiver under.</span><span class="sxs-lookup"><span data-stu-id="09a45-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing NetX Duo&reg; primitives underneath.</span></span> <span data-ttu-id="09a45-106">Både IPv6-och IPv4-protokoll och nätverks adresser stöds.</span><span class="sxs-lookup"><span data-stu-id="09a45-106">Both IPv6 and IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="09a45-107">Detta API-skikt i BSD-Compatible Sockets ska fungera lika snabb eller något snabbare än vanliga BSD-implementeringar eftersom detta API använder interna NetX Duo-primitiver och kringgår onödig fel kontroll av NetX.</span><span class="sxs-lookup"><span data-stu-id="09a45-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX Duo primitives and bypasses unnecessary NetX error checking.</span></span>  

<span data-ttu-id="09a45-108">Med konfigurerbara alternativ kan värd programmet definiera maximalt antal Sockets, maximal storlek för TCP-fönster och djup i lyssnings kön.</span><span class="sxs-lookup"><span data-stu-id="09a45-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="09a45-109">På grund av prestanda-och arkitektur begränsningar stöder detta BSD-Compatible Sockets-API: t inte alla BSD-anrop i BSD.</span><span class="sxs-lookup"><span data-stu-id="09a45-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="09a45-110">Dessutom är inte alla BSD-alternativ tillgängliga för BSD-tjänsterna, särskilt följande:</span><span class="sxs-lookup"><span data-stu-id="09a45-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

  - <span data-ttu-id="09a45-111">\***Välj** _ anrop fungerar med endast fd_set \_ readfds, andra argument i det här anropet, t. ex. writefds, exceptfds stöds inte.</span><span class="sxs-lookup"><span data-stu-id="09a45-111">\***select** _ call works with only fd_set \_readfds, other arguments in this call e.g., writefds, exceptfds are not supported.</span></span>
  - <span data-ttu-id="09a45-112">Argumentet "int Flags" stöds inte för ***send** _-, _*_Recv_*_-, _*_SendTo-_\*_ och _ \*_recvfrom_\*\*-anrop.</span><span class="sxs-lookup"><span data-stu-id="09a45-112">The "int flags" argument is not supported for ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** calls.</span></span> 
  - <span data-ttu-id="09a45-113">API: et för BSD-Compatible socket stöder endast en begränsad uppsättning BSD Sockets-anrop.</span><span class="sxs-lookup"><span data-stu-id="09a45-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="09a45-114">Käll koden är utformad för enkelhet och består endast av två filer, ***nxd_bsd. c** _ och _*_nxd_bsd. h_\*_.</span><span class="sxs-lookup"><span data-stu-id="09a45-114">The source code is designed for simplicity and is comprised of only two files, ***nxd_bsd.c** _ and _*_nxd_bsd.h_\*_.</span></span> <span data-ttu-id="09a45-115">Installationen kräver att du lägger till de här två filerna i build-projektet (inte NetX-biblioteket) och skapar värd programmet som ska använda BSD socket service-anrop.</span><span class="sxs-lookup"><span data-stu-id="09a45-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="09a45-116">Filen _ *_nxd_bsd. h_*\* måste också ingå i program källan.</span><span class="sxs-lookup"><span data-stu-id="09a45-116">The _ *_nxd_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="09a45-117">Exempel på demonstrations filer för både IPv4-och IPv6-baserade program ingår i distributionen som är tillgänglig fritt med NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="09a45-117">Sample demo files for both IPv4 and IPv6  based applications are included with the distribution which is freely available with NetX Duo.</span></span> <span data-ttu-id="09a45-118">Mer information finns i hjälp-och README-filerna som paketeras med BSDCompatible socket-API-paketet.</span><span class="sxs-lookup"><span data-stu-id="09a45-118">Further details are available in the help and Readme files bundled with the BSDCompatible Socket API package.</span></span>

<span data-ttu-id="09a45-119">API: erna för BSD-Compatible Sockets stöder följande API-anrop i BSD:</span><span class="sxs-lookup"><span data-stu-id="09a45-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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