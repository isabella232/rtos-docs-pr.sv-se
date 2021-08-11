---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX PPPoE-klient
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX PPPoE Client-komponenten.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 081fbbd917391a4183488f0fbf124cbd8499c5f8b6d619f7b6cff9f61e6d0bcb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798800"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-client"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX PPPoE-klient

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX PPPoE Client-komponenten.

## <a name="product-distribution"></a>Produktdistribution

PPPoE-klienten för NetX finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Paketet innehåller följande filer:

 - **nx_pppoe_client.h** Rubrikfil för PPPoE-klient för NetX
 - **nx_pppoe_client.c** C-källfil för PPPoE-klient för NetX
 - **nx_pppoe_client.pdf** PDF-beskrivning av PPPoE-klienten för NetX
 - **demo_netx_pppoe_client.c** Demonstration av NetX PPPoE-klienten

## <a name="pppoe-client-installation"></a>PPPoE-klientinstallation

För att kunna använda PPPoE-klienten för NetX ska hela distributionen som nämns ovan kopieras till samma katalog där NetX är installerat. Om NetX till exempel är installerat i katalogen *"\threadx\arm7\green"* *ska filerna nx_pppoe_client.h* *och nx_pppoe_client.c* kopieras till den här katalogen.

## <a name="using-pppoe-client"></a>Använda PPPoE-klient

Det är enkelt att använda PPPoE Client för NetX. I princip måste programkoden innehålla *nx_pppoe_client.h* efter att den *innehåller tx_api.h* *och nx_api.h*, för att kunna använda ThreadX respektive NetX. När *nx_pppoe_client.h* ingår kan programkoden sedan göra de PPPoE-klientfunktionsanrop som anges senare i den här guiden. Programmet måste också inkludera *nx_pppoe_client.c* i byggprocessen. Den här filen måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX PPPoE-klienten.

## <a name="small-example-system"></a>Litet exempelsystem

Följande är ett exempel som illustrerar hur du använder NetX PPPoE Client beskrivs i bild 1.1. I det här exemplet inkluderar PPPoE-klienten *filen nx_pppoe_client.h* på rad 50. Därefter skapas PPPoE-klienten i *"thread_0_entry"* på rad 238. Observera att PPPoE-klienten ska skapas efter att IP-instansen har skapats. IP-instansen och PPP-instansen skapas och initieras rad142-220. PPPoE-klientkontrollblocket *"pppoe_client"* definierades som en global variabel på rad 75 tidigare. Funktionerna för att skicka och ta emot anges på rad 238.

I allmänhet ska PPPoE-modulen användas med PPP-modulen. I det här exemplet tas PPP-klientens *in nx_ppp.h* in på rad 49. Därefter skapas PPP-klienten på rad 164. Rad 172 konfigurera funktionen för att skicka PPP-paket. Rad 179–190 ställer in IP-adresserna och definierar protokollet pap. Rad 104-129 konfigurera användarnamn och lösenord för protokollet pap.

När PPPoE-sessionen har upprättats. Programmet kan anropa nx_pppoe_client_session_get *hämta* sessionsinformationen (serverns MAC-adress och sessions-ID) på rad 264. PPP eller Program kan anropa *nx_pppoe_client_session_packet_send* skicka PPPoE-paket på rad 283.

När programmet inte längre bearbetar PPP-trafik kan programmet anropa nx_pppoe_client_session_terminate *för* att avsluta PPPoE-sessionen.

Observera att i det här exemplet fungerar PPPoE-klienten med en normal IP-stack samtidigt och delar en Ethernet-drivrutin. Skicka samma Ethernet-drivrutin för normal IP-instans på rad 155 och PPPoE-klientinstansen på rad 298.

> [!NOTE]
> Omdefiniera **NX_PHYSICAL_HEADER** till 24 för att säkerställa tillräckligt med utrymme för att fylla i det fysiska huvudet. Fysisk rubrik:14(Ethernet-sidhuvud) + 6(PPPoE-sidhuvud) + 2(PPP-rubrik) + 2(justering med fyra byte).

```c
  1 /**************************************************************************/
  2 /**************************************************************************/
  3 /**                                                                       */
  4 /** NetX PPPoE Client stack Component                                     */
  5 /**                                                                       */
  6 /**   This is a small demo of the high-performance NetX PPPoE Client      */
  7 /**   stack. This demo includes IP instance, PPPoE Client and PPP Client  */
  8 /**   stack. Create one IP instance includes two interfaces to support    */
  9 /**   for normal IP stack and PPPoE Client, PPPoE Client can use the      */
 10 /**   mutex of IP instance to send PPPoE message when share one Ethernet  */
 11 /**   driver. PPPoE Client work with normal IP instance at the same time. */
 12 /**                                                                       */
 13 /**   Note1: Substitute your Ethernet driver instead of                   */
 14 /**   _nx_ram_network_driver before run this demo                         */
 15 /**                                                                       */
 16 /**   Note2: Prerequisite for using PPPoE.                                */
 17 /**   Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling*/
 18 /**   in physical header. Physical header:14(Ethernet header)             */
 19 /**    + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)          */
 20 /**                                                                       */
 21 /**************************************************************************/
 22 /**************************************************************************/
 23
 24
 25       /*****************************************************************/
 26       /*                          NetX Stack                           */
 27       /*****************************************************************/
 28
 29                                             /***************************/
 30                                             /*        PPP Client       */
 31                                             /***************************/
 32
 33                                             /***************************/
 34                                             /*       PPPoE Client      */
 35                                             /***************************/
 36       /***************************/         /***************************/
 37       /*    Normal Ethernet Type */         /*    PPPoE Ethernet Type  */
 38       /***************************/         /***************************/
 39       /***************************/         /***************************/
 40       /*       Interface 0       */         /*       Interface 1       */
 41       /***************************/         /***************************/
 42
 43       /*****************************************************************/
 44       /*                       Ethernet Dirver                         */
 45       /*****************************************************************/
 46
 47 #include   "tx_api.h"
 48 #include   "nx_api.h"
 49 #include   "nx_ppp.h"
 50 #include   "nx_pppoe_client.h"
 51
 52 /* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified
       to match PPPoE moduler under this definition.  */
 53 #ifdef NX_PPP_PPPOE_ENABLE
 54
 55 /* If the driver is not initialized in other module, define NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
       to initialize the driver in PPPoE module .
 56    In this demo, the driver has been initialized in IP module.  */
 57 #ifndef NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
 58
 59 /* Define the block size.  */
 60 #define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
 61 #define     DEMO_STACK_SIZE         2048
 62 #define     PPPOE_THREAD_SIZE       2048
 63
 64 /* Define the ThreadX and NetX object control blocks...  */
 65 TX_THREAD               thread_0;
 66
 67 /* Define the packet pool and IP instance for normal IP instnace.  */
 68 NX_PACKET_POOL          pool_0;
 69 NX_IP                   ip_0;
 70
71 /* Define the PPP Client instance.  */
 72 NX_PPP                  ppp_client;
 73
 74 /* Define the PPPoE Client instance.  */
 75 NX_PPPOE_CLIENT         pppoe_client;
 76
 77 /* Define the counters.  */
 78 CHAR                    *pointer;
 79 ULONG                   error_counter;
 80
 81 /* Define thread prototypes.  */
 82 void    thread_0_entry(ULONG thread_input);
 83
 84 /***** Substitute your PPP driver entry function here *********/
 85 extern void    _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);
 86
 87 /***** Substitute your Ethernet driver entry function here *********/
 88 extern void    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
 89
 90 /* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP.
 91    Functions to be provided by PPP for calling by the PPPoE Stack.  */
 92 void    ppp_client_packet_send(NX_PACKET *packet_ptr);
 93 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr);
 94
 95 /* Define main entry point.  */
 96
 97 int main()
 98 {
 99
100     /* Enter the ThreadX kernel.  */
101     tx_kernel_enter();
102 }
103
104 UINT generate_login(CHAR *name, CHAR *password)
105 {
106
107     /* Make a name and password, called "myname" and "mypassword".  */
108     name[0] = 'm';
109     name[1] = 'y';
110     name[2] = 'n';
111     name[3] = 'a';
112     name[4] = 'm';
113     name[5] = 'e';
114     name[6] = (CHAR) 0;
115
116     password[0] = 'm';
117     password[1] = 'y';
118     password[2] = 'p';
119     password[3] = 'a';
120     password[4] = 's';
121     password[5] = 's';
122     password[6] = 'w';
123     password[7] = 'o';
124     password[8] = 'r';
125     password[9] = 'd';
126     password[10] = (CHAR) 0;
127
128     return(NX_SUCCESS);
129 }
130
131 /* Define what the initial system looks like.  */
132
133 void    tx_application_define(void *first_unused_memory)
134 {
135
136 UINT    status;
137
138     /* Setup the working pointer.  */
139     pointer =  (CHAR *) first_unused_memory;
140
141     /* Initialize the NetX system.  */
142     nx_system_initialize();
143
144     /* Create a packet pool for normal IP instance.  */
145     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
146                                    (1536 + sizeof(NX_PACKET)),
147                                    pointer, NX_PACKET_POOL_SIZE);
148     pointer = pointer + NX_PACKET_POOL_SIZE;
149
150     /* Check for error.  */
151     if (status)
152         error_counter++;
153
154     /* Create an normal IP instance.  */
155     status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 44), 0xFFFFFF00UL,
156                           &pool_0, _nx_ram_network_driver, pointer, 2048, 1);
157     pointer = pointer + 2048;
158
159     /* Check for error.  */
160     if (status)
161         error_counter++;
162
163     /* Create the PPP instance.  */
164     status = nx_ppp_create(&ppp_client, "PPP Instance", &ip_0, pointer, 2048, 1,
165                            &pool_0, NX_NULL, NX_NULL); pointer = pointer + 2048;
166
167     /* Check for PPP create error.   */
168     if (status)
169         error_counter++;
170
171     /* Set the PPP packet send function.  */
172     status = nx_ppp_packet_send_set(&ppp_client, ppp_client_packet_send);
173
174     /* Check for PPP packet send function set error.   */
175     if (status)
176         error_counter++;
177
178     /* Define IP address. This PPP instance is effectively the client since it doesn't have
           any IP addresses. */
179     status = nx_ppp_ip_address_assign(&ppp_client, IP_ADDRESS(0, 0, 0, 0), IP_ADDRESS(0, 0, 0, 0));
180
181     /* Check for PPP IP address assign error.   */
182     if (status)
183         error_counter++;
184
185     /* Setup PAP, this PPP instance is effectively the since it generates the name and password
           for the peer..  */
186     status = nx_ppp_pap_enable(&ppp_client, generate_login, NX_NULL);
187
188     /* Check for PPP PAP enable error.  */
189     if (status)
190         error_counter++;
191
192     /* Attach an interface for PPP.  */
193     status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", IP_ADDRESS(0, 0, 0, 0), 0,
                                        nx_ppp_driver);
194
195     /* Check for error.  */
196     if (status)
197         error_counter++;
198
199     /* Enable ARP and supply ARP cache memory for Normal IP Instance.  */
200     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
201     pointer = pointer + 1024;
202
203     /* Check for ARP enable errors.  */
204     if (status)
205         error_counter++;
206
207     /* Enable ICMP */
208     status = nx_icmp_enable(&ip_0);
209     if(status)
210         error_counter++;
211
212     /* Enable UDP traffic.  */
213     status =  nx_udp_enable(&ip_0);
214     if (status)
215         error_counter++;
216
217     /* Enable TCP traffic.  */
218     status =  nx_tcp_enable(&ip_0);
219     if (status)
220         error_counter++;
221
222     /* Create the main thread.  */
223     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
224                      pointer, DEMO_STACK_SIZE,
225                      4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
226     pointer =  pointer + DEMO_STACK_SIZE;
227
228 }
229
230 /* Define the test threads.  */
231
232 void    thread_0_entry(ULONG thread_input)
233 {
234 UINT    status;
235 ULONG   ip_status;
236
237     /* Create the PPPoE instance.  */
238     status =  nx_pppoe_client_create(&pppoe_client, (UCHAR *)"PPPoE Client",  &ip_0,  0,
        &pool_0, pointer, PPPOE_THREAD_SIZE, 4, _nx_ram_network_driver, pppoe_client_packet_receive);
239     pointer = pointer + PPPOE_THREAD_SIZE;
240     if (status)
241     {
242         error_counter++;
243         return;
244     }
245
246     /* Establish PPPoE Client sessione.  */
247     status = nx_pppoe_client_session_connect(&pppoe_client, NX_WAIT_FOREVER);
248     if (status)
249     {
250         error_counter++;
251         return;
252     }
253
254     /* Wait for the link to come up.  */
255     status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                              &ip_status, NX_WAIT_FOREVER);
256     if (status)
257     {
258         error_counter++;
259         return;
260     }
261
262     /* Get the PPPoE Server physical address and Session ID after establish PPPoE Session.  */
263     /*
264     status = nx_pppoe_client_session_get(&pppoe_client, &server_mac_msw,
                                             &server_mac_lsw, &session_id);
265     if (status)
266         error_counter++;
267     */
268 }
269
270 /* PPPoE Client receive function.  */
271 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr)
272 {
273
274     /* Call PPP Client to receive the PPP data fame.  */
275     nx_ppp_packet_receive(&ppp_client, packet_ptr);
276 }
277
278 /* PPP Client send function.  */
279 void    ppp_client_packet_send(NX_PACKET *packet_ptr)
280 {
281
282     /* Directly Call PPPoE send function to send out the data through PPPoE module.  */
283     nx_pppoe_client_session_packet_send(&pppoe_client, packet_ptr);
284 }
285 #endif /* NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE  */
286
287 #endif /* NX_PPP_PPPOE_ENABLE  */
```

**Bild 1.1 Exempel på PPPoE-klientanvändning med NetX**

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa PPPoE-klienten för NetX. I följande lista beskrivs var och en i detalj:

- **NX_DISABLE_ERROR_CHECKING** Det här alternativet tar bort den grundläggande kontrollen av PPPoE-klientens fel. Det används vanligtvis när programmet har felsökts.
- **NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** Om den definieras aktiverar funktionen för att initiera Ethernet-drivrutinen i PPPoE-modulen. Den inaktiveras som standard.
- **NX_PPPOE_CLIENT_THREAD_TIME_SLICE** Tidssnittsalternativ för PPPoE-klienttråd. Som standard är det här värdet TX_NO_TIME_SLICE.
- **NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** Detta definierar vänte potionen för inledande återöverföring av PADI-paket. Som standard är det här värdet 1 sekund.
- **NX_PPPOE_CLIENT_PADI_COUNT** Detta definierar hur många PADI-överföringsförsök som tillåts innan anslutningen anses vara bruten. Som standard är det här värdet 4.
- **NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** Detta definierar vänte potionen för inledande återöverföring av PADR-paket. Som standard är det här värdet 1 sekund.
- **NX_PPPOE_CLIENT_PADR_COUNT** Detta definierar hur många PADR-överföringsförsök som tillåts innan anslutningen anses vara bruten. Som standard är det här värdet 4.
- **NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** Detta definierar den maximala storleken för AC-Name. Som standard är det här värdet 32.
- **NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** Detta definierar den maximala storleken för AC-Cookie. Som standard är det här värdet 32.
- **NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** Detta definierar den maximala storleken för Relay-Session-Id. Som standard är det här värdet 12.
- **NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** Anger minsta paketnyttolaststorlek för PPPoE-klienten. Om paketnyttolastens storlek är större än det här värdet kan du undvika paketkedjeindelade. Som standard är det här värdet 1520 (maximal nyttolaststorlek på Ethernet 1500, Ethernet-rubrik 14, CRC 2 och justering med fyra byte 4).
