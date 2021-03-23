---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Point-to-Point Protocol-tjänster (PPP)
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo PPP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825824"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Point-to-Point Protocol-tjänster (PPP)

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo PPP-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_ppp_byte_receive**: *ta emot en byte från serie-ISR*
- **nx_ppp_chap_challenge**: *skapa en CHAP-utmaning*
- **nx_ppp_chap_enable**: *Aktivera CHAP-autentisering*
- **nx_ppp_create**: *skapa en PPP-instans*
- **nx_ppp_delete**: *ta bort en PPP-instans*
- **nx_ppp_dns_address_get**: *Hämta DNS-serverns IP-adress*
- **nx_ppp_dns_address_set**:*Ange DNS-serverns IP-adress*
- **nx_ppp_secondary_dns_address_get**: *Hämta IP-adress för sekundär DNS-Server*
- **nx_ppp_secondary_dns_address_set**: *Ange IP-adress för Secondary_DNS Server*
- **nx_ppp_interface_index_get**: *Hämta IP-gränssnitts index*
- **nx_ppp_ip_address_assign**: *tilldela IP-adresser för IPCP*
- **nx_ppp_link_down_notify**: *meddela programmet vid en länk*
- **nx_ppp_link_up_notify**: *meddela programmet vid länkning*
- **nx_ppp_nak_authentication_notify**: *meddela program om autentiserings-NAK tas emot*
- **nx_ppp_pap_enable**: *aktivera PAP-autentisering*
- **nx_ppp_ping_request**: *skicka en LCP ECHO-begäran*
- **nx_ppp_raw_string_send**: *skicka icke-PPP-sträng*
- **nx_ppp_restart**: *starta om PPP-bearbetning*
- **nx_ppp_start**: *Starta PPP-bearbetning*
- **nx_ppp_status_get**: *Hämta aktuell PPP-status*
- **nx_ppp_stop**: *stoppa PPP-bearbetning*
- **nx_ppp_packet_receive**: *ta emot PPP-paket*
- **nx_ppp_packet_send_set**: *Konfigurera funktionen för att skicka PPP-paket*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Ta emot en byte från serie-ISR

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anropas vanligt vis från programmets (ISR) driv rutin för seriell driv rutins tjänsten för att överföra mottagna byte till PPP. Vid anrop placerar den här rutinen mottagna byte i en cirkelformad byte-buffert och meddelar lämplig PPP-tråd för bearbetning.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **byte**: byte mottaget från seriell enhet

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-byte-mottagning.
- **NX_PPP_BUFFER_FULL**: (0XB1) PPP Serial buffer är redan full.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Trådar, ISR: er

### <a name="example"></a>Exempel

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

Generera en CHAP-utmaning

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en CHAP-utmaning när PPP-anslutningen redan är igång. Detta ger programmet möjlighet att verifiera anslutningens äkthet på regelbunden basis. Om utmaningen Miss lyckas stängs PPP-länken.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-utmaning har initierats.
- **NX_PPP_FAILURE**: (0XB0) ogiltig PPP-utmaning. CHAP har bara Aktiver ATS för Response.
- **NX_NOT_IMPLEMENTED**: (0X80) CHAP-logik har inaktiverats via NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

Aktivera CHAP-autentisering

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar CHAP (Challenge-Handshake Authentication Protocol) för den angivna PPP-instansen.

Om funktions pekarna "***get_challenge_values**_" och "_ * _get_verification_values_* *" anges, krävs CHAP av den här PPP-instansen. Annars svarar CHAP bara på motpartens utmanings begär Anden.

Det finns flera data objekt som refereras till nedan i de nödvändiga callback-funktionerna. Data objektets *hemlighet*, *namn* och *system* förväntas vara null-terminerade strängar med en maximal storlek på NX_PPP_NAME_SIZE-1. Data objekt *rand_value* förväntas vara en null-avslutad sträng med en maximal storlek på NX_PPP_VALUE_SIZE-1. Dataobjektets *ID* är en enkel osignerad tecken typ.

>[!NOTE]
> Den här funktionen måste anropas efter *nx_ppp_create* men innan nx_ip_create eller *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **get_challenge_values**: pekare till program funktion för att hämta värden som används för utmaningen. Observera att värdena för *rand_value*, *ID* och *hemlighet* måste kopieras till de angivna målen.
- **get_responder_values**: pekare till program funktion som hämtar värden som används för att svara på en utmaning. Observera att värdena *system*, *Name* och *Secret* måste kopieras till de angivna målen.
- **get_verification_values**: pekare till program funktion som hämtar värden som används för att verifiera utmanings svaret. Observera att värdena *system*,*Name* och *Secret* måste kopieras till de angivna målen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades PPP CHAP Enable
- **NX_NOT_IMPLEMENTED**: (0X80) CHAP-logik har inaktiverats via NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller callback-funktions pekare. Observera att om *get_challenge_values* har angetts måste även *get_verification_values* -funktionen anges.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a>nx_ppp_create

Skapa en PPP-instans

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en PPP-instans för den angivna NetX IP-instansen. Den här funktionen måste anropas innan NetX-IP-instansen skapas.

>[!NOTE]
> Det är vanligt vis en bra idé att skapa NetX IP-tråd med högre prioritet än PPP-Trådens prioritet. Mer information om hur du anger prioritet för IP-tråd finns i *nx_ip_create* -tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **namn**: namnet på den här PPP-instansen.
- **ip_ptr**: pekare till kontroll block för en icke-skapad IP-instans.
- **stack_memory_ptr**: pekare för att starta PPP-trådens stack Area.
- **stack_size**: storlek i byte i trådens stack.
- **pool_ptr**: pekar mot standardpaket-poolen.
- **thread_priority**: prioritet för interna PPP-trådar (1-31).
- **ppp_invalid_packet_handler**: funktions pekare till program hanterare för alla icke-PPP-paket. NetX PPP anropar vanligt vis den här rutinen under initieringen. Det är här som programmet kan svara på modem kommandon eller i Windows XP. NetX PPP-applikationen kan initiera PPP genom att svara på "klient SERVER" till den första "klienten" som skickas av Windows XP.
- **ppp_byte_send**: funktions pekare till programmets serie byte-utdata.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-skapande.
- NX_PTR_ERROR: (0x07) ogiltig PPP-, IP-eller byte-utmatnings funktion.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

Ta bort en PPP-instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den tidigare skapade PPP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-borttagning.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Hämta IP-adress för DNS-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar DNS-IP-adressen som anges av peer-datorn i IPCP-handskakningen. Om ingen IP-adress angavs av peer-datorn returneras en IP-adress på 0.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **dns_address_ptr**: målet för DNS-serveradressen

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad DNS-adress Hämta.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="example"></a>Exempel

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Hämta IP-adress för sekundär DNS-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den sekundära DNS-IP-adressen som anges av peer-datorn i IPCP-handskakningen. Om ingen IP-adress angavs av peer-datorn returneras en IP-adress på 0.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **dns_address_ptr**: mål för sekundär DNS-serveradress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad DNS-adress Hämta.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="example"></a>Exempel

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Ange IP-adress för primär DNS-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-adressen för DNS-servern. Om peer-servern skickar en DNS-Server Option-begäran i IPCP-tillstånd, kommer den här värden att tillhandahålla informationen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **dns_address**: DNS-serveradress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) en DNS-adress uppsättning har slutförts.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Ange IP-adress för sekundär DNS-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-adressen för den sekundära DNS-servern. Om peer skickar en sekundär DNS-Server Options-begäran i IPCP-läget, kommer den här värden att tillhandahålla informationen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **dns_address**: sekundär DNS-serveradress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) en DNS-adress uppsättning har slutförts. 
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Hämta IP-gränssnitts index

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det IP-gränssnitts index som är associerat med denna PPP-instans. Detta är endast användbart om PPP-instansen inte är det primära gränssnittet för en IP-instans.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **index_ptr**: målet för gränssnitts index

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades PPP-index Hämta.
- **NX_IN_PROGRESS**: (0X37) PPP har inte slutfört initieringen.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

Tilldela IP-adresser för IPCP

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar lokala och peer-IP-adresser för användning i IPCP-protokollet (Internet Protocol Control Protocol). Den ska anropas för PPP-instansen som har giltiga IP-adresser för sig och den andra peer-datorn.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **local_ip_address**: lokal IP-adress.
- **peer_ip_address**: peer-datorns IP-adress.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutförde PPP-adresstilldelning.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Meddela programmet vid en länk

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar programmets länk ned meddelande återanrop med den angivna PPP-instansen. Om det inte är NULL anropas programmets länk ned callback-funktion när länken slutar fungera.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **link_down_callback**: program varans länk ned meddelande funktions pekare. Om det här värdet är NULL inaktive ras länk ned meddelande.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutförd länk för att registrera meddelande återanrop.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="example"></a>Exempel

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

Avisera program vid länkning

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Beskrivning

Den här tjänsten registrerar programmets länk upp ett meddelande återanrop med den angivna PPP-instansen. Om det inte är NULL anropas programmets länk för motringning när länken visas.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **link_up_callback**: programmets länk för meddelande funktions pekare. Om det här värdet är NULL är länkat meddelande inaktiverat. * *

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) länkad registrering av meddelande återanrop.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="example"></a>Exempel

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

Meddela program om autentisering NAK tas emot

### <a name="prototype"></a>Prototyp

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar programmets autentiserings-NAK meddelande återanrop med den angivna PPP-instansen. Om den inte är NULL anropas den här återanrops funktionen när PPP-instansen får en NAK under authentiaction.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **nak_authentication_notify**: pekare till funktion som anropas när PPP-instansen får en autentiserings-NAK. Om värdet är NULL är meddelandet inaktiverat.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) registreringen av återanrop i meddelande lyckades.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="example"></a>Exempel

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

Aktivera PAP-autentisering

### <a name="prototype"></a>Prototyp

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar PAP-protokollet (Password Authentication Protocol) för den angivna PPP-instansen. Om funktions pekaren "***verify_login***" anges krävs PAP av den här PPP-instansen. Annars svarar PAP endast på motpartens PAP-krav som anges under LCP-förhandlingen.

Det finns flera data objekt som refereras till nedan i de nödvändiga callback-funktionerna. Data objektets *namn* förväntas vara null-avslutad sträng med en maximal storlek på NX_PPP_NAME_SIZE-1. *Lösen ordet* för data objekt förväntas också vara en null-avslutad sträng med en maximal storlek på NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Den här funktionen måste anropas efter *nx_ppp_create* men innan *nx_ip_create* eller *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **generate_login**: pekare till program funktion som skapar ett *namn* och *lösen ord* för autentisering av peer-datorn. Observera att värdena för *namn* och *lösen ord* måste kopieras till de angivna målen.
- **verify_login**: pekare till program funktion som verifierar det *namn* och *lösen ord* som anges av peer-datorn. Den här rutinen måste jämföra det angivna *namnet* och *lösen ordet*. Om den här rutinen returnerar NX_SUCCESS är namnet och lösen ordet rätt och PPP kan fortsätta till nästa steg. Annars returnerar den här rutinen NX_PPP_ERROR och PPP bara väntar på ett annat namn och lösen ord.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) SLUTFÖRDE PPP PAP enable.
- **NX_NOT_IMPLEMENTED**: (0X80) PAP-logiken inaktiverades via NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller program funktions pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

Skicka en LCP ping-begäran

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en LCP-begäran och anger en flagga som PPP-enheten väntar på ett eko svar. Alternativet vänta är primärt för *nx_packet_allocate* -anropet. Tjänsten returnerar så fort begäran skickas. Det väntar inte på svar. 

När ett matchande eko svar tas emot, tar PPP-trådens aktivitet bort flaggan. PPP-enheten måste ha slutfört LCP-delen av PPP-förhandlingen.

Den här tjänsten är användbar för PPP-konfiguration där det inte går att avsöka maskin vara för länk status.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **data**: pekare till data som ska skickas i ekobegäran.
- **data_size**: storleken på de data som ska skickas wait_option tid att vänta på att skicka LCP-eko meddelandet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad begäran om ekobegäran.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) PPP-anslutningen har inte upprättats.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller program funktions pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Program trådar

### <a name="example"></a>Exempel

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

Skicka en RAW ASCII-sträng

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en icke-PPP ASCII-sträng direkt ut PPP-gränssnittet. Den används vanligt vis när PPP får ett icke-PPP-paket som innehåller information om modem kontroll.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **string_ptr**: pekare till sträng som ska skickas.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP RAW-sträng skicka.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare eller sträng pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

Starta om PPP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar om PPP-bearbetningen. Det kallas vanligt vis när länken måste upprättas igen antingen från en länk ned motringning eller av ett modem som inte är ett PPP-meddelande som anger att kommunikationen bröts.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-omstart initierad.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

Starta PPP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar PPP-bearbetningen. Den anropas vanligt vis efter att nx_ppp_stop () anropades.

>[!NOTE]
> PPP startar automatiskt PPP-bearbetningen när länken är aktive rad.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) en lyckad PPP-start har initierats. 
- **NX_PPP_ALREADY_STARTED**: (0XB9) PPP har redan startats.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

Hämta aktuell PPP-status

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar aktuell status för den angivna PPP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **status_ptr**: målet för PPP-statusen är följande möjliga status värden:
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> Statusen är bara giltig om API: et returnerar NX_SUCCESS. Om något av värdena för * _FAILED returneras, stoppas dessutom PPP-bearbetningen tills det startas om igen av programmet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-status-begäran.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar, timers, ISR: er

### <a name="example"></a>Exempel

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

Starta PPP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar PPP-bearbetningen. Användaren kan också anropa nx_ppp_start () för att starta PPP-bearbetningen om det behövs.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) en lyckad PPP-start har initierats. 
- **NX_PPP_ALREADY_STOPPED**: (0XB8) PPP har redan stoppats.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

Ta emot PPP-paket

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>Beskrivning

Den här tjänsten tar emot PPP-paket.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **packet_ptr**: pekar mot PPP-paket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-status-begäran.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Ange funktionen Skicka PPP-paket

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Beskrivning

Den här tjänsten anger PPP-paketets sändnings-funciton.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr**: pekar mot PPP-kontroll block.
- **nx_ppp_packet_send**: rutin för att skicka PPP-paket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad PPP-status-begäran.
- NX_PTR_ERROR: (0x07) ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```