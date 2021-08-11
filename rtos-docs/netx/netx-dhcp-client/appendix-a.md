---
title: Bilaga A – Beskrivning av funktionen för återställningstillstånd
description: Med Azure RTOS netX DHDP-klientkonfigurationsalternativet, NX_DHCP_CLIENT_RESTORE_STATE, kan ett system återställa en tidigare skapad DHCP-klientpost i ett bundet tillstånd mellan omstarter av systemet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4b7286726eb6bfc666ba7a4b9983847da442fe212a45f4b28e184f70cf46e2b4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801248"
---
# <a name="appendix-a---description-of-the-restore-state-feature"></a>Bilaga A – Beskrivning av funktionen för återställningstillstånd

Med Azure RTOS netX DHDP-klientkonfigurationsalternativet, NX_DHCP_CLIENT_RESTORE_STATE, kan ett system återställa en tidigare skapad DHCP-klientpost i ett bundet tillstånd mellan omstarter av systemet.

När det här alternativet är aktiverat kan programmet pausa och återuppta DHCP-klienttråden. Det finns också en tjänst för att uppdatera DHCP-klienten med förfluten tid mellan att pausa och återuppta tråden.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Återställa DHCP-klienten mellan omstarter

Innan du återställer en DHCP-klient efter omstart, tilldelas en tidigare skapad DHCP-klient som måste nå det bundna tillståndet och tilldelas en IP-adress från DHCP-servern. Innan DHCP-programmet aktiveras måste det spara den aktuella DHCP-klientposten till icke-beständigt minne. Det måste också finnas en oberoende "tids keeper" någon annanstans i systemet för att hålla reda på den tid som förflutit under detta avstängda tillstånd. När programmet aktiveras skapar det en ny INSTANS av DHCP-klienten och uppdaterar den sedan med den tidigare skapade DHCP-klientposten. Den förflutna tiden hämtas från "time keeper" och tillämpas sedan på den tid som återstår på DHCP-klientlånet. Observera att detta kan göra att DHCP-klienten ändrar tillstånd, t.ex. från BOUND till RENEWING. I det här läget kan programmet återuppta DHCP-klienten.

Om tiden som förflutit under strömavbrottet försätter DHCP-klientens tillstånd i antingen RENEW- eller REBIND-tillstånd, initierar DHCP-klienten automatiskt DHCP-meddelanden som begär att förnya eller binda OM IP-adresslånet. Om IP-adressen har upphört att gälla rensar DHCP-klienten automatiskt IP-adressen på IP-instansen och påbörjar DHCP-processen från INIT-tillståndet och begär en ny IP-adress.

På det här sättet kan DHCP-klienten fungera mellan omstarter som om den inte avbryts.

Nedan visas en illustration av den här funktionen. Detta förutsätter att DHCP-klienten endast körs på det primära gränssnittet.

```C
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{


  /* No previously saved Client record. Start the DHCP Client in the INIT state. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  do
  {
  
    /* Wait for DHCP to assign the IP address. */
  } while (status != NX_SUCCESS);

  /* We have a valid IP address. */

  /* At some point decide we power down the system. */

  /* Save the Client state data which we will subsequently need to restore the DHCP  
     Client. */
  status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);         

  /* Copy this memory to non-volatile memory (not shown). */

  /* Delete the IP and DHCP Client instances before powering down. */
  nx_dhcp_delete(&dhcp_0);

  nx_ip_delete(&ip_0);

  /* Ready to power down, having released other resources as necessary. */

}
else
{

  /* The application has determined there is a previously saved record. We will 
     restore it to the current DHCP Client instance. */

  /* Get the previous Client state data from non-volatile memory. */

  /* Apply the record to the current Client instance. This will also 
     update the IP instance with IP address, mask etc. */
  status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

     if (status != NX_SUCCESS)
      return;

     /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
     status = nx_dhcp_resume(&dhcp_0);

     if (status != NX_SUCCESS)
      return;

}
```

## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Återuppta DHCP-klienttråden efter stängning 

Om du vill pausa en DHCP-klienttråd utan att stänga av anropar *programmet nx_dhcp_suspend* på en DHCP-klient som har uppnått TILLSTÅNDET BOUND och som har en giltig IP-adress. När den är redo att återuppta DHCP-klienten anropar den *först nx_dhcp_client_update_time_remaining* för att uppdatera tiden som återstår på DHCP-adresslånet (att få den tid som förflutit från en oberoende tids keeper). Sedan anropas nx_dhcp_resume *för* att återuppta DHCP-klienttråden.

Om den tid som förflutit försätter DHCP-klienttillståndet i antingen RENEW- eller REBIND-tillstånd initierar DHCP-klienten automatiskt DHCP-meddelanden som begär att förnya eller binda OM IP-adresslånet. Om IP-adressen har upphört att gälla rensar DHCP-klienten automatiskt IP-adressen och påbörjar DHCP-processen från INIT-tillståndet och begär en ny IP-adress.

Nedan visas en illustration av hur du använder den här funktionen.

```C
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   
    /* Wait for DHCP to obtain an IP address. */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the 
     network... */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the
     elapsed time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}
```

Nedan visas en lista över tjänster för att återställa ett DHCP-klienttillstånd från minnet och för att pausa och återuppta DHCP-klienten.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Skapa en post för det aktuella DHCP-klienttillståndet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, 
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Description

Den här tjänsten sparar DHCP-klienten som körs på det första gränssnittet som är aktiverat för DHCP som finns på DHCP-klientinstansen till den post som record_ptr. Detta gör att DHCP-klientprogrammet kan återställa sitt DHCP-klienttillstånd efter exempelvis ett strömavbrott och en omstart.

Om du vill spara en DHCP-klientpost i ett visst gränssnitt om fler än ett gränssnitt är aktiverat för DHCP använder *du nx_dhcp_interface_client_get_record* tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **record_ptr** Pekare till DHCP-klientpost

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klientpost som skapats

- **NX_DHCP_NOT_BOUND** (0x94) Klienten är inte i bunden tillstånd

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Inga gränssnitt har aktiverats för DHCP

- **NX_PTR_ERROR** (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

Skapa en post för det aktuella DHCP-klienttillståndet i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, 
                                 UINT interface_index,
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```
### <a name="description"></a>Description

Den här tjänsten sparar DHCP-klienten som körs på det angivna gränssnittet till den post som record_ptr. Detta gör att DHCP-klientprogrammet kan återställa sitt DHCP-klienttillstånd efter exempelvis ett strömavbrott och en omstart.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **interface_index** Index som du vill hämta post för

- **record_ptr** Pekare till DHCP-klientpost

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klientpost som skapats

- **NX_DHCP_NOT_BOUND** (0x94) Klienten är inte i bunden tillstånd

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Ogiltigt gränssnittsindex

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_ client_restore_record

Återställa DHCP-klienten från en tidigare sparad post

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD       
                                    *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Description

Med den här tjänsten kan ett program återställa sin DHCP-klient från en tidigare session med hjälp av DHCP-klientposten som record_ptr. Den time_elapsed indata tillämpas på den tid som återstår på DHCP-klientlånet.

Detta kräver att DHCP-klientprogrammet skapade en post för DHCP-klienten innan den stängas av och sparade posten i icke-volatilt minne.

Om fler än ett gränssnitt är aktiverat för DHCP-klienten, tillämpas den här tjänsten på det första giltiga gränssnittet som finns i DHCP-klientinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **record_ptr** Pekare till DHCP-klientpost

- **time_elapsed** Tid att subtrahera från den återstående lånetiden i indataklientposten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klientpost återställd

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Inga gränssnitt som kör DHCP

- **NX_PTR_ERROR** (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

Återställa DHCP-klienten från en tidigare sparad post i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD       
                                              *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Description

Med den här tjänsten kan ett program återställa sin DHCP-klient i det angivna gränssnittet med hjälp av DHCP-klientposten som record_ptr. Den time_elapsed indata tillämpas på den tid som återstår på DHCP-klientlånet.

Detta kräver att DHCP-klientprogrammet skapade en post för DHCP-klienten innan den stängas av och sparade posten i icke-volatilt minne.

Om fler än ett gränssnitt är aktiverat för DHCP-klienten, tillämpas den här tjänsten på det första giltiga gränssnittet som finns i DHCP-klientinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **record_ptr** Pekare till DHCP-klientpost

- **time_elapsed** Tid att subtrahera från den återstående lånetiden i indataklientposten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klientpost återställd

- **NX_DHCP_NOT_BOUND** (0x94) Klienten är inte bunden till IP-adressen

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Ogiltigt gränssnittsindex

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_ client_update_time_remaining

Uppdatera tiden som återstår för DHCP-klientlån

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr
                                           ULONG time_elapsed);
```
### <a name="description"></a>Description

Den här tjänsten uppdaterar den tid som återstår på DHCP-klientens IP-adresslån med time_elapsed indata i det första gränssnittet aktiverat för DHCP som finns på DHCP-klientinstansen. Programmet måste pausa DHCP-klienttråden innan den här tjänsten används med *hjälp av nx_dhcp_suspend*. När du har anropat den här tjänsten kan programmet återuppta DHCP-klienttråden genom att *anropa nx_dhcp_resume*.

Detta är avsett för DHCP-klientprogram som behöver pausa DHCP-klienttråden under en viss tidsperiod och sedan uppdatera den återstående IP-adresslåntiden.

> [!NOTE]
> Den här tjänsten är inte avsedd att användas *med* nx_dhcp_client_get_record och *nx_dhcp_client_restore_record* beskrivs ovan). Dessa tjänster beskrivs tidigare i det här avsnittet.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **time_elapsed** Tid att subtrahera från tiden som återstår för IP-adresslånet

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klientens IP-lån har uppdaterats

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Inga gränssnitt har aktiverats för DHCP

- **NX_PTR_ERROR** (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

Uppdatera tiden som återstår för DHCP-klientlån i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```
### <a name="description"></a>Description

Den här tjänsten uppdaterar tiden som återstår på DHCP-klientens IP-adresslån med time_elapsed indata i det angivna gränssnittet om gränssnittet är aktiverat för DHCP. Programmet måste pausa DHCP-klienttråden innan den här tjänsten används med *hjälp av nx_dhcp_suspend*. När du har anropat den här tjänsten kan programmet återuppta DHCP-klienttråden genom att *anropa nx_dhcp_resume*. Observera att pausa och återuppta DHCP-klienttråden gäller för alla gränssnitt som är aktiverade för DHCP.

Detta är avsett för DHCP-klientprogram som behöver pausa DHCP-klienttråden under en viss tidsperiod och sedan uppdatera den återstående IP-adresslåntiden.

> [!NOTE] 
> Den här tjänsten är inte avsedd att användas *med* nx_dhcp_client_get_record och *nx_dhcp_client_restore_record* beskrivs ovan). Dessa tjänster beskrivs tidigare i det här avsnittet.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **interface_index** Index till gränssnitt för att tillämpa förfluten tid på

- **time_elapsed** Tid att subtrahera från tiden som återstår för IP-adresslånet

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klientens IP-lån har uppdaterats

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Ogiltigt gränssnittsindex

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

Pausa DHCP-klienttråden

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Description

Den här tjänsten pausar den aktuella DHCP-klienttråden. Observera att *till skillnad nx_dhcp_stop* finns det ingen ändring i DHCP-klienttillståndet när den här tjänsten anropas.

Den här tjänsten inaktiverar DHCP som körs på alla gränssnitt som är aktiverade för DHCP.

Information om hur du uppdaterar DHCP-klienttillståndet med förfluten tid när DHCP-klienten pausas finns i *nx_dhcp_client_update_time_remaining* beskrivs ovan. Om du vill återuppta en inaktiverad DHCP-klienttråd ska programmet anropa *nx_dhcp_resume*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klienttråden pausas

- **NX_PTR_ERROR** (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```


## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Återuppta en inaktiverad DHCP-klienttråd

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Description

Den här tjänsten återupptar en inaktiverad DHCP-klienttråd. Observera att det inte finns någon ändring i det faktiska DHCP-klienttillståndet efter att klienttråden har återupptas. Information om hur du uppdaterar tiden som återstår på DHCP-klientens IP-adresslån med förfluten tid innan du anropar *nx_dhcp_resume* finns *i nx_dhcp_client_update_time_remaining* beskrivs ovan.

Den här tjänsten återupptar DHCP som körs på alla gränssnitt som är aktiverade för DHCP.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x0) Klienttråden återupptas

- NX_PTR_ERROR (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```