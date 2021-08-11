---
title: Kapitel 3 – Beskrivning Azure RTOS Tjänster för NetX Point-to-Point Protocol (PPP)
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo PPP-tjänster (listas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1174d7fdc470bc91278413d56948789cc210aab9d7389a5ecad5baf4f6ad7a7f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798086"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a>Kapitel 3 – Beskrivning Azure RTOS Tjänster för NetX Point-to-Point Protocol (PPP)

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo PPP-tjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nx_ppp_byte_receive:** *Ta emot en byte från serie-ISR*
- **nx_ppp_chap_challenge:** Generera *en CHAP-utmaning*
- **nx_ppp_chap_enable:** Aktivera *CHAP-autentisering*
- **nx_ppp_create:** Skapa *en PPP-instans*
- **nx_ppp_delete:** Ta *bort en PPP-instans*
- **nx_ppp_dns_address_get:** Hämta *IP-adress för DNS-server*
- **nx_ppp_dns_address_set:** Ange *IP-adress för DNS-server*
- **nx_ppp_secondary_dns_address_get:** Hämta *IP-adress för sekundär DNS-server*
- **nx_ppp_secondary_dns_address_set:** Ange *IP Secondary_DNS serveradress*
- **nx_ppp_interface_index_get:** Hämta *IP-gränssnittsindex*
- **nx_ppp_ip_address_assign:** Tilldela *IP-adresser för IPCP*
- **nx_ppp_link_down_notify:** Meddela *programmet via länk ned*
- **nx_ppp_link_up_notify:** *Meddela programmet via länk*
- **nx_ppp_nak_authentication_notify:** Meddela *programmet om autentiseringEN ÄR MOTTAGEN*
- **nx_ppp_pap_enable:** *Aktivera PAP-autentisering*
- **nx_ppp_ping_request:** Skicka *en LCP-ekobegäran*
- **nx_ppp_raw_string_send:** Skicka *icke-PPP-sträng*
- **nx_ppp_restart:** Starta *om PPP-bearbetning*
- **nx_ppp_start:** Starta *PPP-bearbetning*
- **nx_ppp_status_get:** *Hämta aktuell PPP-status*
- **nx_ppp_stop:** *Stoppa PPP-bearbetning*
- **nx_ppp_packet_receive:** *Ta emot PPP-paket*
- **nx_ppp_packet_send_set:** Ange *funktionen skicka PPP-paket*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Ta emot en byte från serie-ISR

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Description

Den här tjänsten anropas vanligtvis från programmets isr (Serial driver Interrupt Service Routine) för att överföra en mottagen byte till PPP. När den här rutinen anropas placerar den mottagna byten i en cirkulär bytebuffert och meddelar lämplig PPP-tråd för bearbetning.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **byte:** Byte som tagits emot från serieenheten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-byte-mottagning.
- **NX_PPP_BUFFER_FULL:**(0xB1) PPP-seriebufferten är redan full.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, ISR

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

### <a name="description"></a>Description

Den här tjänsten initierar en CHAP-utmaning när PPP-anslutningen redan är igång. Detta ger programmet möjlighet att regelbundet verifiera anslutningens äkthet. Om utmaningen misslyckas stängs PPP-länken.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-utmaning initierad.
- **NX_PPP_FAILURE**: (0xB0) Ogiltig PPP-utmaning, CHAP aktiverades endast för svar.
- **NX_NOT_IMPLEMENTED**: (0x80) CHAP-logik har inaktiverats via NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten aktiverar Challenge-Handshake AUTHENTICATION Protocol (CHAP) för den angivna PPP-instansen.

Om funktionspekaren **"* get_challenge_values**_" och "_ get_verification_values **" anges krävs CHAP av den här * PPP-instansen. Annars svarar CHAP bara på peer-peerns utmaningsbegäranden.

Det finns flera dataobjekt som refereras nedan i de återanropsfunktioner som krävs. Dataobjektens *hemlighet,* *namn* och *system* förväntas vara NULL-avslutade strängar med en maximal storlek på NX_PPP_NAME_SIZE-1. Dataobjektet som *rand_value* förväntas vara en NULL-avslutad sträng med en maximal storlek på NX_PPP_VALUE_SIZE-1. Dataobjektets *ID* är en enkel osignerad teckentyp.

>[!NOTE]
> Den här funktionen måste anropas *efter nx_ppp_create* men innan du nx_ip_create eller *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **get_challenge_values**: Pekare till programfunktion för att hämta värden som används för utmaningen. Observera att *värdena rand_value,* *id* och *hemligt* måste kopieras till de angivna destinationerna.
- **get_responder_values:** Pekare till programfunktion som hämtar värden som används för att svara på en utmaning. Observera att *systemvärdena*, *namnvärdena* *och de hemliga* värdena måste kopieras till de angivna målen.
- **get_verification_values:** Pekare till programfunktion som hämtar värden som används för att verifiera utmaningssvaret. Observera att *systemvärdena*,*namnvärdena* *och de hemliga* värdena måste kopieras till de angivna målen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP CHAP-aktivera
- **NX_NOT_IMPLEMENTED**: (0x80) CHAP-logik har inaktiverats via NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare eller återanropsfunktions pekare. Observera att *om get_challenge_values* anges måste *även get_verification_values-funktionen* anges.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en PPP-instans för den angivna NetX IP-instansen. Den här funktionen måste anropas innan du skapar NetX IP-instansen.

>[!NOTE]
> Det är vanligtvis en bra idé att skapa NetX IP-tråden med högre prioritet än PPP-trådprioritet. Mer information om *hur du anger IP-trådprioritet* finns i nx_ip_create-tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **name**: Namnet på den här PPP-instansen.
- **ip_ptr:** Pekare för att styra block för IP-instanser som inte har skapats ännu.
- **stack_memory_ptr:** Pekare för att starta PPP-trådens stackområde.
- **stack_size:** Storlek i byte i trådens stack.
- **pool_ptr:** Pekare till standardpaketpoolen.
- **thread_priority:** Prioritet för interna PPP-trådar (1–31).
- **ppp_invalid_packet_handler:** Funktionspekare till programmets hanterare för alla icke-PPP-paket. NetX PPP anropar vanligtvis den här rutinen under initieringen. Det är här som programmet kan svara på modemkommandon eller när det gäller Windows XP kan NetX PPP-programmet initiera PPP genom att svara med" KLIENTSERVER" på den första "KLIENT" som skickas av Windows XP.
- **ppp_byte_send:** Funktionspekare till programmets utdatarutin för seriebyte.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP-skapa.
- NX_PTR_ERROR: (0x07) Markör för ogiltig PPP-, IP- eller byte-utdatafunktion.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort den tidigare skapade PPP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-borttagning.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Hämta IP-adress för DNS-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar DNS-IP-adressen som tillhandahålls av peer i IPCP-handskakningen. Om ingen IP-adress har angetts av peer-datorn returneras IP-adressen 0.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **dns_address_ptr:** Mål för DNS-serveradress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DNS-adress hämta.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

### <a name="example"></a>Exempel

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Hämta IP-adress för sekundär DNS-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den sekundära DNS IP-adressen som tillhandahålls av peer i IPCP-handskakningen. Om ingen IP-adress har angetts av peer-datorn returneras IP-adressen 0.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **dns_address_ptr:** Mål för sekundär DNS-serveradress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DNS-adress hämta.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

### <a name="example"></a>Exempel

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Ange primär IP-adress för DNS-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Description

Den här tjänsten anger IP-adressen för DNS-servern. Om peer-datorn skickar en begäran om DNS-serveralternativ i IPCP-tillstånd anger den här värden informationen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **dns_address:** DNS-serveradress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DNS-adressuppsättning.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Ange sekundär IP-adress för DNS-server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Description

Den här tjänsten anger den sekundära IP-adressen för DNS-servern. Om peer-datorn skickar en sekundär BEGÄRAN om DNS-serveralternativ i IPCP-tillstånd anger den här värden informationen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **dns_address:** Sekundär DNS-serveradress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad DNS-adressuppsättning. 
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP har inte slutfört förhandling med peer.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Hämta IP-gränssnittsindex

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hämtar IP-gränssnittsindexet som är associerat med den här PPP-instansen. Detta är endast användbart när PPP-instansen inte är det primära gränssnittet för en IP-instans.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **index_ptr:** Mål för gränssnittsindex

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP-index get.
- **NX_IN_PROGRESS:**(0x37) PPP har inte slutfört initieringen.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten uppsättningar lokala och peer-IP-adresser för användning i Internet Protocol Control Protocol (IPCP). Den bör anropas för den PPP-instans som har giltiga IP-adresser för sig själv och den andra peer-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **local_ip_address:** Lokal IP-adress.
- **peer_ip_address:** Peers IP-adress.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-adresstilldelning.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Meddela programmet via länk ned

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Description

Den här tjänsten registrerar programmets länk till återanrop av meddelanden med den angivna PPP-instansen. Om den inte är NULL anropas programmets återanropsfunktion med länk nedåt när länken går ned.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **link_down_callback:** Pekaren för programmets länk nedåt i meddelandefunktionen. Om NULL är länkning av meddelande inaktiverat.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad länkning av registrering för återanrop av meddelanden.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

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

Meddela programmet vid länk

### <a name="prototype"></a>Prototyp

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Description

Den här tjänsten registrerar programmets återanrop av meddelanden med den angivna PPP-instansen. Om den inte är NULL anropas programmets återanropsfunktion när länken visas.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **link_up_callback:** Programmets länk upp meddelandefunktions pekare. Om NULL är länkmeddelandet inaktiverat.**

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad länkning av registrering för återanrop av meddelanden.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

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

Meddela programmet om autentiseringEN ÄR mottagen

### <a name="prototype"></a>Prototyp

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Description

Den här tjänsten registrerar programmets återanrop av autentiseringsmeddelande med den angivna PPP-instansen. Om den inte är NULL anropas den här återanropsfunktionen när PPP-instansen tar emot en NULL under autentiseringen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **nak_authentication_notify:** Pekaren till funktionen anropas när PPP-instansen tar emot autentiseringEN SNAPO. Om NULL är meddelandet inaktiverat.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Registrering av motringning av meddelanden har lyckats.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

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

### <a name="description"></a>Description

Den här tjänsten aktiverar PAP (Password Authentication Protocol) för den angivna PPP-instansen. Om ***funktionspekaren " verify_login***" anges krävs PAP av den här PPP-instansen. I annat fall svarar PAP endast på peerns PAP-krav som anges under LCP-förhandlingen.

Det finns flera dataobjekt som refereras nedan i de återanropsfunktioner som krävs. Dataobjektets *namn* förväntas vara NULL-avslutad sträng med en maximal storlek på NX_PPP_NAME_SIZE-1. Lösenordet för *dataobjektet* förväntas också vara en NULL-avslutad sträng med en maximal storlek på NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Den här funktionen måste anropas *efter nx_ppp_create* men *innan nx_ip_create* eller *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **generate_login:** Pekare till programfunktion som skapar ett *namn och* *lösenord för* autentisering av peer-datorn. Observera att värdena *för* namn *och* lösenord måste kopieras till de angivna destinationerna.
- **verify_login:** Pekare till programfunktion som verifierar det *namn och* lösenord *som anges* av peer-datorn. Den här rutinen måste jämföra det angivna *namnet* och *lösenordet*. Om rutinen returnerar NX_SUCCESS är namnet och lösenordet korrekta och PPP kan fortsätta till nästa steg. Annars returnerar den här rutinen NX_PPP_ERROR och PPP väntar bara på ett annat namn och lösenord.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP PAP-aktivera.
- **NX_NOT_IMPLEMENTED**: (0x80) PAP-logik har inaktiverats via NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare eller programfunktionspekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

Skicka en LCP-pingbegäran

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Description

Den här tjänsten skickar en LCP-begäran och anger en flagga att PPP-enheten väntar på ett ekosvar. Väntealternativet är främst för det *nx_packet_allocate anropet.* Tjänsten returnerar när begäran skickas. Den väntar inte på ett svar. 

När ett matchande ekosvar tas emot rensar PPP-trådaktiviteten flaggan. PPP-enheten måste ha slutfört LCP-delen av PPP-förhandlingen.

Den här tjänsten är användbar för PPP-installation där det inte är möjligt att avse maskinvaran efter länkstatus.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **data**: Pekare till data som ska skickas i ekobegäran.
- **data_size:** Storleken på data som ska skickas wait_option väntetiden för att skicka LCP-ekomeddelandet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad skickad ekobegäran.
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) PPP-anslutning upprättas inte.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare eller programfunktionspekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Programtrådar

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

Skicka en ASCII-råsträng

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar en ICKE-PPP ASCII-sträng direkt från PPP-gränssnittet. Det används vanligtvis när PPP tar emot ett icke-PPP-paket som innehåller information om modemkontroll.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **string_ptr: Pekare** till sträng som ska skickas.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP-råsträngssändning.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare eller sträng pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten startar om PPP-bearbetningen. Den anropas vanligtvis när länken måste upprättas igen antingen från en återanrop av en länk ned eller via ett icke-PPP-modemmeddelande som anger att kommunikationen har gått förlorad.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP-omstart initierad.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten startar PPP-bearbetningen. Den anropas vanligtvis efter nx_ppp_stop() anropas.

>[!NOTE]
> PPP startar automatiskt PPP-bearbetningen när länken är aktiverad.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad PPP-start initierad. 
- **NX_PPP_ALREADY_STARTED:**(0xb9) PPP har redan startats.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten hämtar den aktuella statusen för den angivna PPP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **status_ptr:** Målet för PPP-statusen är följande möjliga statusvärden:
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
> Statusen är endast giltig om API:et returnerar NX_SUCCESS. Om något av *_FAILED-statusvärdena returneras stoppas PPP-bearbetningen tills den startas om igen av programmet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-statusbegäran.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar, timers, ISR

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

### <a name="description"></a>Description

Den här tjänsten stoppar PPP-bearbetningen. Användaren kan också anropa nx_ppp_start() för att starta PPP-bearbetningen om det behövs.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-start initierad. 
- **NX_PPP_ALREADY_STOPPED:**(0xb8) PPP har redan stoppats.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten tar emot PPP-paket.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **packet_ptr:** Pekare till PPP-paket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-statusbegäran.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Ange funktionen skicka PPP-paket

### <a name="prototype"></a>Prototyp

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Description

Den här tjänsten anger hur PPP-paketet ska skickas.

### <a name="input-parameters"></a>Indataparametrar

- **ppp_ptr:** Pekare till PPP-kontrollblock.
- **nx_ppp_packet_send:** Rutin för att skicka PPP-paket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad PPP-statusbegäran.
- NX_PTR_ERROR: (0x07) Ogiltig PPP-pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```