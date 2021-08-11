---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX BSD
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX BSD-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c04175ec18dff160faf853d675c9c85c9a0c6fbc5e834c410a7cb97a739c69f8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796709"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX BSD

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX BSD-komponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX BSD kan hämtas från vår offentliga källkodsdatabas på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_bsd.h:** Rubrikfil för NetX BSD
- **nx_bsd.c:** C-källfil för NetX BSD
- **nx_bsd.pdf:** Användarhandbok för NetX BSD

Demofiler:
- **bsd_demo_tcp.c**
- **bsd_demo_udp.c**

## <a name="netx-bsd-installation"></a>NetX BSD-installation

För att kunna använda NetX BSD ska hela distributionen som nämns ovan kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*" ska *filerna nx_bsd.h* *och nx_bsd.c* kopieras till den här katalogen.

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>Skapa ThreadX- och NetX-komponenterna i ett BSD-program

### <a name="threadx"></a>ThreadX

ThreadX-biblioteket måste definiera *bsd_errno* i den lokala trådlagringen. Vi rekommenderar följande procedur:

1. I *tx_port.h* anger du ett av TX_THREAD_EXTENSION makron enligt följande:

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. Återskapa ThreadX-biblioteket.

> [!NOTE]
> Om TX_THREAD_EXTENSION_3 redan används kan användaren använda något av de andra TX_THREAD_EXTENSION makron.

### <a name="netx"></a>Netx

Innan du använder NetX BSD Services måste NetX-biblioteket byggas med NX_ENABLE_EXTENDED_NOTIFY_SUPPORT (t.ex. *i nx_user.h*). Som standard definieras den inte.

## <a name="using-netx-bsd"></a>Använda NetX BSD

Det är enkelt att använda BSD för NetX. I princip måste programkoden innehålla *nx_bsd.h* efter att den *innehåller tx_api.h* och *nx_api.h* för att kunna använda ThreadX respektive NetX. När *nx_bsd.h* ingår kan programkoden använda de BSD-tjänster som anges senare i den här guiden. Programmet måste även innehålla *nx_bsd.c* i byggprocessen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX BSD.

Om du vill använda NetX BSD-tjänster måste programmet skapa en IP-instans, en paketpool och initiera BSD-tjänster genom att *anropa bsd_initialize.* Detta visas i avsnittet "Litet exempel" senare i den här guiden. Prototypen visas nedan:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

De sista tre parametrarna används för att skapa en tråd för att utföra periodiska uppgifter, till exempel söka efter TCP-händelser och definiera trådstackutrymmet.

> [!NOTE]
> Till skillnad från BSD-sockets, som fungerar i network bye-ordning, fungerar NetX i värdbyteordningen för värdprocessorn. Av källkompatibilitetsskäl har makrona htons(), nt maskinvaru(), htonl(), ntohl() definierats, men ändrar inte det argument som skickas.

## <a name="netx-bsd-limitations"></a>NetX BSD-begränsningar

På grund av prestanda- och arkitekturproblem stöder NetX BSD inte alla BSD 4.3 socket-funktioner:

INT-flaggor stöds inte för *anropen send, recv, sendto* *och recvfrom.*

## <a name="netx-bsd-with-dns-support"></a>NetX BSD med DNS-stöd

Om NX_BSD_ENABLE_DNS har definierats kan NetX BSD skicka DNS-frågor för att hämta värdnamn eller värd-IP-information. Den här funktionen kräver att en NetX DNS-klient har skapats tidigare med *hjälp nx_dns_create tjänsten.* En eller flera kända IP-adresser för DNS-servern måste registreras med *DNS-instansen* med hjälp av nx_dns_server_add för att lägga till serveradresser.

DNS-tjänster och minnesallokering används av *getaddrinfo-* och *getnameinfo-tjänster:*

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

När BSD-programmet anropar *getaddrinfo* med ett värdnamn anropar NetX BSD någon av nedanstående tjänster för att hämta IP-adressen:

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

För *nx_dns_ipv4_address_by_name_get* använder NetX BSD de ipv4_addr_buffer minnesområdena. Storleken på dessa buffertar definieras av ( `NX_BSD_IPV4_ADDR_PER_HOST * 4` ).

För att returnera adressinformation från *getaddrinfo* använder NetX BSD ThreadX-blockminnestabellen *nx_bsd_addrinfo_pool_memory*, vars minnesområde definieras av en annan uppsättning konfigurerbara *alternativ, NX_BSD_IPV4_ADDR_MAX_NUM*.

Se **Konfigurationsalternativ** för mer information om konfigurationsalternativen ovan.

Om en NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats och värdindata är ett kanoniskt namn, allokerar NetX BSD minne dynamiskt från en blockpool som skapats *tidigare _nx_bsd_cname_block_pool*

> [!NOTE]
> När *du har anropat getaddrinfo* ansvarar BSD-programmet för att frigöra minnet som res-argumentet pekar på tillbaka till blocktabellen med hjälp av *freeaddrinfo-tjänsten.*

## <a name="configuration-options"></a>Konfigurationsalternativ

Med användarkonfigurerbara alternativ *i nx_bsd.h* kan programmet finjustera NetX BSD-sockets för sina specifika krav. Följande är en lista över dessa parametrar:

- **NX_BSD_TCP_WINDOW: Används** i TCP socket create-anrop. 65535 är en typisk fönsterstorlek för 100 MB Ethernet. Standardvärdet är 65535.
- **NX_BSD_SOCKFD_START** Det här är det logiska indexet för startvärdet för BSD-socketfilen. Som standard är det här alternativet 32.
- **NX_BSD_MAX_SOCKETS** Anger det maximala antalet totalt antal sockets som är tillgängliga i BSD-lagret och måste vara en multipel av 32. Värdet är standardvärdet 32.
- **NX_BSD_SOCKET_QUEUE_MAX** Anger det maximala antalet UDP-paket som lagras i kön för ta emot socket. Värdet är som standard 5.
- **NX_BSD_MAX_LISTEN_BACKLOG** Detta anger storleken på lyssnarkön (' eftersläpning') för BSD TCP-sockets. Standardvärdet är 5.
- **NX_MICROSECOND_PER_CPU_TICK** Anger antalet mikrosekunder per timeravbrott
- **NX_BSD_TIMEOUT** Anger timeout i timer tick för interna NetX-anrop som krävs av BSD. Standardvärdet är 20*NX_IP_PERIODIC_RATE.
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT:** Anger timeout-värdet i timern för NetX-frånkopplingsanrop. Standardvärdet är 1.
- **NX_BSD_PRINT_ERRORS** Om det är inställt returneras felstatus för en BSD-funktion som returnerar ett radnummer och en typ av fel, till exempel NX_SOC_ERROR där felet inträffar. Detta kräver att programutvecklaren definierar felsökningsutdata. Standardinställningen är inaktiverad och inga felsökningsutdata anges i *nx_bsd.h*
- **NX_BSD_TIMER_RATE** Intervall efter vilket den periodiska BSD-timeraktiviteten körs. Standardvärdet är 1 sekund (1 * NX_IP_PERIODIC_RATE).
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER** Om detta anges tillåter det här alternativet att BSD-timeout-processen körs i systemtimerkontexten. Standardbeteendet är inaktiverat. Den här funktionen beskrivs i detalj i kapitel 2 "Installation och användning av NetX BSD".
- **NX_BSD_ENABLE_DNS** Om aktiverad skickar NetX BSD en DNS-fråga för ett värdnamn eller en värd-IP-adress. Kräver att en DNS-klientinstans skapas och startas tidigare. Som standard är den inte aktiverad.
- **NX_BSD_IPV4_ADDR_MAX_NUM** Maximalt antal IPv4-adresser som returneras *av getaddrinfo*. Detta tillsammans med NX_BSD_IPV4_ADDR_MAX_NUM definierar storleken på NetX BSD-blockpoolen nx_bsd_addrinfo_block_pool för att dynamiskt allokera minne till adressinformationslagring i *getaddrinfo*. Standardvärdet är 5.
- **NX_BSD_IPV4_ADDR_PER_HOST: Definierar** maximalt antal IPv4-adresser som lagras per DNS-fråga. Standardvärdet är 5.

## <a name="bsd-socket-options"></a>Alternativ för BSD Socket

Följande lista över NetX BSD-socketalternativ kan aktiveras (eller inaktiveras) vid körning per socket med *tjänsten setsockopt:*

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

Det finns två olika inställningar för *option_level*.

Den första typen av socketalternativ för körningstid är SOL_SOCKET alternativ för socketnivå. Om du vill aktivera ett alternativ på socketnivå anropar du *setsockopt* med option_level inställt på SOL_SOCKET och option_name angett till det specifika alternativet, t.ex. SO_BROADCAST. Om du vill hämta en alternativinställning *anropar du getsockopt* för option_name med option_level återigen inställd på SOL_SOCKET.

Listan över alternativ på socketnivå för körningstid visas nedan.

- **SO_BROADCAST:** Om det här är inställt kan du skicka och ta emot broadcast-paket från Netx-sockets. Det här är standardbeteendet för NetX. Alla sockets har den här funktionen.
- **SO_ERROR:** Används för att hämta socketstatus för den tidigare socketåtgärden för den angivna socketen med *hjälp av getsockopt-tjänsten.* Alla sockets har den här funktionen.
- **SO_KEEPALIVE:** Om detta anges aktiveras TCP Keep Alive-funktionen. Detta kräver att NetX-biblioteket byggs med NX_TCP_ENABLE_KEEPALIVE definieras *i nx_user.h*. Den här funktionen är inaktiverad som standard.
- **SO_RCVTIMEO:** Anger väntealternativet i sekunder för att ta emot paket på NetX BSD-sockets. Standardvärdet är NX_WAIT_FOREVER (0xFFFFFFFF) eller, om icke-blockerande är aktiverat, NX_NO_WAIT (0x0).
- **SO_RCVBUF:** Anger fönsterstorleken för TCP-socketen. Standardvärdet, som NX_BSD_TCP_WINDOW, är inställt på 64k för BSD TCP-sockets. Om du vill ange storleken över 65535 måste NetX-biblioteket byggas med NX_TCP_ENABLE_WINDOW_SCALING definieras.
- **SO_REUSEADDR:** Om det här anges gör detta att flera sockets kan mappas till en port. Den vanligaste användningen är för TCP-serversocketen. Det här är standardbeteendet för NetX-sockets.

Den andra typen av socketalternativ för körningstid är IP-alternativnivån. Om du vill aktivera ett alternativ för IP-nivå anropar du *setsockopt* med option_level inställt på IP_PROTO och option_name till alternativet t.ex. IP_MULTICAST_TTL. Om du vill hämta en alternativinställning *anropar du getsockopt* för option_name med option_level återigen inställd på IP_PROTO.

Listan över ip-nivåalternativ för körningstid visas nedan.

- **IP_MULTICAST_TTL:** Detta anger hur lång tid UDP-sockets ska vara. Standardvärdet är NX_IP_TIME_TO_LIVE (0x80) när socketen skapas. Det här värdet kan åsidosättas genom att anropa *setsockopt med det* här socketalternativet.
- **IP_ADD_MEMBERSHIP:** Om det här alternativet har angetts kan BSD-socketen (gäller endast UDP-socketar) ansluta till den angivna IGMP-gruppen.
- **IP_DROP_MEMBERSHIP:** Om det här alternativet har angetts kan BSD-socketen (gäller endast UDP-socketar) lämna den angivna IGMP-gruppen.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur du använder NetX BSD visas i bild 1.0 nedan. I det här exemplet kommer *indelningsfilen nx_bsd.h* på rad 7. Därefter skapas *IP-bsd_ip* och *bsd_pool* som globala variabler på rad 20 och 21. Observera att den här demonstrationen använder en RAM-drivrutin (virtuell) (rad 41). Klienten och servern delar samma IP-adress på en enskild IP-instans i det här exemplet.

Klient- och servertrådarna skapas på rad 303 och 309 *i tx_application_define* som uppsättningar programmet och definieras på raderna 293-361. När IP-instansen har skapats på rad 327 aktiveras IP-instansen för TCP-tjänster på rad 350. Det sista kravet innan BSD-tjänster kan användas är att *anropa bsd_initialize* på rad 360 för att konfigurera alla datastrukturer och NetX- och ThreadX-resurser som krävs av BSD.

I servertrådens postfunktion *thread_1_entry,* som definieras på raderna 381–397, väntar programmet på att drivrutinen ska initiera NetX med nätverksparametrar. När det är klart anropar den *tcpServer,* som definieras på raderna 146–253, för att hantera information om hur du konfigurerar TCP-serversocketen.

*tcpServer* skapar huvudsocketen genom att anropa *sockettjänsten* på rad 159 och binda den till lyssningssocketen med hjälp av bindningsanropet på rad 176.  Den konfigureras sedan för att lyssna efter anslutningsbegäranden på rad 191. Observera att huvudsocketen inte accepterar en anslutningsbegäran. Den körs i en kontinuerlig loop som anropar *select* varje gång för att identifiera anslutningsbegäranden. En sekundär BSD-socket som väljs från en matris med BSD-sockets tilldelas anslutningsbegäran efter anrop till *accepttjänsten* på rad 218.

På klientsidan bör klienttrådens *postfunktion, thread_0_entry*, som definierats på raderna 366-377, också vänta tills NetX initieras av drivrutinen. Här väntar vi bara på att serversidan ska göra det. Den anropar *sedan tcpClient* som definierats på rad 54-142 för att hantera informationen om att konfigurera TCP-klientsocketen och begära en TCP-anslutning.

TCP-klientsocketen skapas på rad 68. Socketen är bunden till den angivna IP-adressen och försöker ansluta till TCP-servern genom att *anropa connect* på rad 84. Den är nu redo att börja skicka och ta emot paket.

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
