---
title: Bilaga A – Beskrivning av funktionen återställnings tillstånd
description: Klient konfigurations NX_DHCP_CLIENT_RESTORE_STATE alternativet för Azure återställnings tider NetX DHDP, gör det möjligt för ett system att återställa en tidigare skapad DHCP-klient post i ett begränsat tillstånd mellan omstarter av systemet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be8b5dc4885951bee3dba38af6fe5e21b81aa767
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826808"
---
# <a name="appendix-a---description-of-the-restore-state-feature"></a>Bilaga A – Beskrivning av funktionen återställnings tillstånd

Klient konfigurations NX_DHCP_CLIENT_RESTORE_STATE alternativet för Azure återställnings tider NetX DHDP, gör det möjligt för ett system att återställa en tidigare skapad DHCP-klient post i ett begränsat tillstånd mellan omstarter av systemet.

När det här alternativet är aktiverat kan programmet pausa och återuppta DHCP-klientens tråd. Det finns också en tjänst för att uppdatera DHCP-klienten med förfluten tid mellan att pausa och återuppta tråden.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Återställa DHCP-klienten mellan omstarter

Innan du återställer en DHCP-klient efter omstart, måste du ha en tidigare skapad DHCP-klient som måste komma åt bindnings statusen och tilldelas en IP-adress från DHCP-servern. Innan den stängs av måste DHCP-programmet spara den aktuella posten för DHCP-klienten till icke-flyktigt minne. Det måste också finnas en oberoende "tidsbehållare" i systemet för att hålla reda på hur lång tid som förflutit under det här läget är avstängd. Vid inaktive rad skapar programmet en ny DHCP-klient instans och uppdaterar den sedan med den tidigare skapade DHCP-klientprogramvaran. Tiden som förflutit hämtas från "tids hållaren" och tillämpas sedan på den tid som återstår av DHCP-klientens lån. Observera att detta kan leda till att DHCP-klienten ändrar tillstånd, t. ex. från gräns till FÖRNYAnde. I det här läget kan programmet återuppta DHCP-klienten.

Om den tid som förflutit under avstängning ger DHCP-klientens tillstånd antingen förnyelse eller OMBINDNING, initierar DHCP-klienten automatiskt DHCP-meddelanden som begär att förnya eller ombinda IP-adresslån. Om IP-adressen har upphört att gälla rensar DHCP-klienten automatiskt IP-adressen på IP-instansen och startar DHCP-processen från INIT-tillståndet och begär en ny IP-adress.

På så sätt kan DHCP-klienten arbeta mellan omstarter som om de är avbrutna.

Nedan visas en illustration av den här funktionen. Detta förutsätter att DHCP-klienten bara körs på det primära gränssnittet.

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

## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Återuppta DHCP-klientens tråd efter avbrott 

Om du vill pausa en DHCP-klient tråd utan att stänga av, anropar programmet *nx_dhcp_suspend* på en DHCP-klient som har uppnått bindnings status och som har en giltig IP-adress. När den är redo att återuppta DHCP-klienten anropas den först *nx_dhcp_client_update_time_remaining* för att uppdatera tiden som återstår av DHCP-adresslån (hämtning av den tid som förflutit från en oberoende tids hållare). Sedan anropas *nx_dhcp_resume* för att återuppta DHCP-klientens tråd.

Om den tid som förflutit sätter DHCP-klientens tillstånd i antingen förnyelse-eller återbinding-tillstånd initierar DHCP-klienten automatiskt DHCP-meddelanden som begär att förnya eller ombinda IP-adresslån. Om IP-adressen har upphört att gälla rensar DHCP-klienten automatiskt IP-adressen och startar DHCP-processen från INIT-tillståndet och begär en ny IP-adress.

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

Nedan visas en lista över tjänster för att återställa en DHCP-klients tillstånd från minnet och för att pausa och återuppta DHCP-klienten.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Skapa en post med det aktuella DHCP-klientens tillstånd

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, 
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten sparar DHCP-klienten som körs på det första gränssnittet som är aktiverat för DHCP som finns på DHCP-klientcertifikatet till posten som pekas på av record_ptr. Detta gör att DHCP-klientprogrammet kan återställa sitt DHCP-klient tillstånd efter, till exempel en avstängning och omstart.

Om du vill spara en DHCP-resurspost på ett gränssnitt om fler än ett gränssnitt har Aktiver ATS för DHCP använder du tjänsten *nx_dhcp_interface_client_get_record* .

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **record_ptr** Pekare till posten DHCP-klient

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0)-klient posten skapades

- **NX_DHCP_NOT_BOUND** -klienten (0x94) är inte i ett begränsat tillstånd

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt har Aktiver ATS för DHCP

- **NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

Skapa en post för det aktuella DHCP-klientens tillstånd på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, 
                                 UINT interface_index,
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten sparar DHCP-klienten som körs på det angivna gränssnittet till posten som pekas av record_ptr. Detta gör att DHCP-klientprogrammet kan återställa sitt DHCP-klient tillstånd efter, till exempel en avstängning och omstart.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **interface_index** Index som posten ska hämtas till

- **record_ptr** Pekare till posten DHCP-klient

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0)-klient posten skapades

- **NX_DHCP_NOT_BOUND** -klienten (0x94) är inte i ett begränsat tillstånd

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0X9A) ogiltigt gränssnitts index

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

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
### <a name="description"></a>Beskrivning

Den här tjänsten gör det möjligt för ett program att återställa sin DHCP-klient från en tidigare session med hjälp av DHCP-klienttjänsten som record_ptr. Time_elapsed-indatatypen används för den tid som återstår på DHCP-klientens lån.

Detta kräver att DHCP-klientprogrammet skapar en post för DHCP-klienten innan den stängs av och sparar posten till ett beständigt minne.

Om fler än ett gränssnitt är aktiverat för DHCP-klienten, tillämpas den här tjänsten på det första giltiga gränssnittet som finns i DHCP-klientens instans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **record_ptr** Pekare till posten DHCP-klient

- **time_elapsed** Tid för att ta bort från den återstående låne tiden i posten för indata-klienten

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0)-klient posten har återställts

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt som kör DHCP

- **NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Återställa DHCP-klienten från en tidigare sparad post på ett visst gränssnitt

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD       
                                              *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Beskrivning

Den här tjänsten gör det möjligt för ett program att återställa DHCP-klienten på det angivna gränssnittet med hjälp av DHCP-klienttjänsten som record_ptr. Time_elapsed-indatatypen används för den tid som återstår på DHCP-klientens lån.

Detta kräver att DHCP-klientprogrammet skapar en post för DHCP-klienten innan den stängs av och sparar posten till ett beständigt minne.

Om fler än ett gränssnitt är aktiverat för DHCP-klienten, tillämpas den här tjänsten på det första giltiga gränssnittet som finns i DHCP-klientens instans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **record_ptr** Pekare till posten DHCP-klient

- **time_elapsed** Tid för att ta bort från den återstående låne tiden i posten för indata-klienten

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0)-klient posten har återställts

- **NX_DHCP_NOT_BOUND** -klienten (0x94) är inte kopplad till IP-adress

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0X9A) ogiltigt gränssnitts index

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Uppdatera tiden kvar på DHCP-klientens lån

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr
                                           ULONG time_elapsed);
```
### <a name="description"></a>Beskrivning

Den här tjänsten uppdaterar den tid som återstår på DHCP-klientens IP-adresslån med time_elapsed indata för det första gränssnittet som har Aktiver ATS för DHCP som finns på DHCP-klientens instans. Programmet måste pausa klient tråden för DHCP innan du använder den här tjänsten med hjälp av *nx_dhcp_suspend*. När den här tjänsten har anropats kan programmet återuppta DHCP-klient tråden genom att anropa *nx_dhcp_resume*.

Detta är avsett för DHCP-klientprogram som behöver pausa DHCP-klientens tråd under en viss tids period och sedan uppdatera IP-adressens låne tid kvar.

> [!NOTE]
> Den här tjänsten är inte avsedd att användas med *nx_dhcp_client_get_record* och *nx_dhcp_client_restore_record* som beskrivs ovan). Dessa tjänster beskrivs tidigare i det här avsnittet.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **time_elapsed** Tid att ta bort från den tid som återstår av IP-adresslån

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0) klientens IP-lån har uppdaterats

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt har Aktiver ATS för DHCP

- **NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Uppdatera tiden kvar på DHCP-klientcertifikatet i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```
### <a name="description"></a>Beskrivning

Den här tjänsten uppdaterar den tid som återstår på DHCP-klientens IP-adresslån med time_elapsed indata på det angivna gränssnittet om gränssnittet är aktiverat för DHCP. Programmet måste pausa klient tråden för DHCP innan du använder den här tjänsten med hjälp av *nx_dhcp_suspend*. När den här tjänsten har anropats kan programmet återuppta DHCP-klient tråden genom att anropa *nx_dhcp_resume*. Obs! Om du pausar och återupptar återställningen av DHCP-klienten gäller alla gränssnitt som är aktiverade för DHCP.

Detta är avsett för DHCP-klientprogram som behöver pausa DHCP-klientens tråd under en viss tids period och sedan uppdatera IP-adressens låne tid kvar.

> [!NOTE] 
> Den här tjänsten är inte avsedd att användas med *nx_dhcp_client_get_record* och *nx_dhcp_client_restore_record* som beskrivs ovan). Dessa tjänster beskrivs tidigare i det här avsnittet.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

- **interface_index** Indexera till gränssnitt för att använda förfluten tid för

- **time_elapsed** Tid att ta bort från den tid som återstår av IP-adresslån

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0) klientens IP-lån har uppdaterats

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0X9A) ogiltigt gränssnitts index

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Pausa klient tråden för DHCP

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten pausar den aktuella DHCP-klient tråden. Observera att till skillnad från *nx_dhcp_stop* sker ingen ändring av DHCP-klientens tillstånd när denna tjänst anropas.

Den här tjänsten inaktiverar DHCP som körs på alla gränssnitt som är aktiverade för DHCP.

Om du vill uppdatera DHCP-klientens tillstånd med förfluten tid medan DHCP-klienten har pausats, se den *nx_dhcp_client_update_time_remaining* som beskrivs ovan. Om du vill återuppta en pausad DHCP-klient tråd bör programmet anropa *nx_dhcp_resume*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0) klient tråden har pausats

- **NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```


## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Återuppta en pausad DHCP-klient tråd

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten återupptar en pausad DHCP-klient tråd. Observera att den faktiska statusen för DHCP-klienten inte ändras efter att klient tråden har återupptagits. Om du vill uppdatera den återstående tiden i DHCP-klientens IP-adresslån med förfluten tid innan du anropar *nx_dhcp_resume*, se *nx_dhcp_client_update_time_remaining* som beskrivs ovan.

Den här tjänsten återupptar DHCP som körs på alla gränssnitt som är aktiverade för DHCP.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-klient

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x0) klient tråden har återupptagits

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```