---
title: Bilaga A – Beskrivning av funktionen för återställningstillstånd för Azure RTOS NetX Duo DHCPv6-klient
description: Med Azure RTOS netX Duo DHDPv6-klientkonfigurationsalternativet, NX_DHCPV6_CLIENT_RESTORE_STATE, kan ett system återställa en tidigare skapad DHCP-klient i ett bundet tillstånd mellan omstarter av systemet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6840f89e66d713b1839ac84427b73273b3f9601d4b6d9d39cd94908ac77a77ca
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791337"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>Bilaga A – Beskrivning av funktionen för återställningstillstånd för Azure RTOS NetX Duo DHCPv6-klient

Med Azure RTOS netX Duo DHDPv6-klientkonfigurationsalternativet, NX_DHCPV6_CLIENT_RESTORE_STATE, kan ett system återställa en tidigare skapad DHCP-klient i ett bundet tillstånd mellan omstarter av systemet.

Det här alternativet gör också att ett program kan pausa DHCPv6-klienttråden och återuppta den, uppdaterad med tiden mellan att pausa och återuppta tråden utan att stänga av.

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>Återställa DHCPv6-klienten mellan omstarter

För att återställa en DHCPv6-klient mellan omstarter skapar DHCPv6-programmet en instans av DHCPv6-klienten och hämtar sedan ett IP-adresslån med hjälp av det normala DHCPv6-protokollet och anropar *nx_dhcpv6_start*. DHCPv6-programmet väntar sedan på att protokollet ska slutföras. Om allt går bra uppnår enheten BOUND-tillståndet med en tilldelad giltig IP-adress från sin DHCPv6-server. Innan den inaktiveras sparar DHCPv6-klientprogrammet den aktuella DHCPv6-klientinstansen till en DHCPv6-klientpost som sedan lagras i beständigt minne. En oberoende "tids keeper" någon annanstans i systemet håller reda på den tid som förflutit under detta nedstängda tillstånd. Vid strömförsörjningen skapar programmet en ny DHCPv6-klientinstans och uppdaterar den sedan med den tidigare skapade DHCPv6-klientposten. Den förflutna tiden hämtas från "time keeper" och tillämpas sedan på den tid som återstår på DHCP Clientv6-lånet. Nu kan programmet återuppta DHCPv6-klienten.

Om tiden som förflutit under strömavbrottet försätter DHCPv6-klientens tillstånd i antingen RENEW- eller REBIND-tillstånd, initierar DHCPv6-klienten automatiskt DHCPv6-meddelanden som begär att förnya eller binda OM IP-adresslånet. Om IP-adressen har upphört att gälla rensar DHCPv6-klienten automatiskt IP-adressen på IP-instansen och påbörjar DHCPv6-processen från INIT-tillståndet och begär en ny IP-adress.

På det här sättet kan DHCPv6-klienten fungera mellan omstarter som om de avbryts.

Nedan visas en illustration av den här funktionen.

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a>nx_dhcpv6_client_get_record

Skapa en post för det aktuella DHCPv6-klienttillståndet

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Description

Den här tjänsten sparar DHCPv6-klienten till den post som record_ptr. Detta gör att DHCPv6-klientprogrammet kan återställa sitt DHCPv6-klienttillstånd efter exempelvis ett strömavbrott och en omstart.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient

- **record_ptr** Pekare till DHCPv6-klientpost

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS (0x0)** Giltig klientpost har skapats

- **NX_DHCPV6_NOT_BOUND** (0xE94) Klienten är inte i bundet tillstånd, därför inte tilldelad giltig IP-adress

- **NX_PTR_ERROR** (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_client_restore_record

## <a name="nx_dhcpv6_client_restore_record"></a>nx_dhcpv6_client_restore_record

Återställa DHCPv6-klienttillståndet från sparad post

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Description

Med den här tjänsten kan ett DHCPv6-program återskapa sitt DHCPv6-klienttillstånd från en tidigare session genom att uppdatera DHCPv6-klienten med DHCPv6-klientposten som record_ptr pekar på och uppdaterar den återstående tiden på DHCPv6-klientlånet med time_elapsed-indata. Detta gör att DHCPv6-klientprogrammet kan återskapa sin DHCPv6-klient, till exempel efter att den har varit i drift. Detta kräver att DHCPv6-klientprogrammet skapade en post för DHCPv6-klienten innan den stängas av och sparade posten i icke-beständigt minne.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient

- **record_ptr** Pekare till DHCPv6-klientpost

- **time_elapsed** Tid att subtrahera från den återstående lånetiden i indataklientposten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS (0x0)** Klientposten har återställts

- NX_PTR_ERROR (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_client_get_record