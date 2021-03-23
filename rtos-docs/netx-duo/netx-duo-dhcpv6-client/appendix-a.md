---
title: Bilaga A – Beskrivning av funktionen återställnings tillstånd för Azure återställnings tider NetX Duo DHCPv6-klienten
description: Konfigurations alternativet för Azure återställnings tider NetX Duo DHDPv6-klienten NX_DHCPV6_CLIENT_RESTORE_STATE, gör det möjligt för ett system att återställa en tidigare skapad DHCP-klient i ett begränsat tillstånd mellan omstarter av systemet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826100"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>Bilaga A – Beskrivning av funktionen återställnings tillstånd för Azure återställnings tider NetX Duo DHCPv6-klienten

Konfigurations alternativet för Azure återställnings tider NetX Duo DHDPv6-klienten NX_DHCPV6_CLIENT_RESTORE_STATE, gör det möjligt för ett system att återställa en tidigare skapad DHCP-klient i ett begränsat tillstånd mellan omstarter av systemet.

Det här alternativet gör det också möjligt för ett program att pausa DHCPv6-klient tråden och återuppta den, uppdaterat med den tid som förflutit mellan att pausa och återuppta tråden utan att behöva stänga av den.

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>Återställa DHCPv6-klienten mellan omstarter

För att återställa en DHCPv6-klient mellan omstarter skapar DHCPv6-programmet en instans av DHCPv6-klienten och erhåller sedan ett IP-adresslån med det normala DHCPv6-protokollet och anropar *nx_dhcpv6_start*. DHCPv6-programmet väntar sedan på att protokollet ska slutföras. Om alla går bra, uppnår enheten BINDNINGs tillstånd med en tilldelad giltig IP-adress från DHCPv6-servern. Innan den stängs av sparar DHCPv6-klient programmet den aktuella DHCPv6-klient instansen till en DHCPv6-klient post som sedan lagras i beständigt minne. En oberoende "tidsbehållare" i systemet håller reda på den tid som förflutit under det här tillstånd som är avstängd. Vid inaktive rad skapar programmet en ny DHCPv6-klient instans och uppdaterar den sedan med den tidigare skapade DHCPv6-klient posten. Tiden som förflutit hämtas från "tids hållaren" och tillämpas sedan på den tid som återstår av DHCP-Clientv6 lån. I det här läget kan programmet återuppta DHCPv6-klienten.

Om den tid som förflutit under avstängning ger DHCPv6-klientens tillstånd i antingen förnyelse eller OMBINDNING, initierar DHCPv6-klienten automatiskt DHCPv6-meddelanden som begär att förnya eller ombinda IP-adresslån. Om IP-adressen har upphört att gälla rensar DHCPv6-klienten automatiskt IP-adressen på IP-instansen och påbörjar DHCPv6-processen från INIT-tillståndet och begär en ny IP-adress.

På så sätt kan DHCPv6-klienten köras mellan omstarter som om de är avbrutna.

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

Skapa en post för aktuellt DHCPv6-klient tillstånd

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten sparar DHCPv6-klienten till posten som pekas av record_ptr. Detta gör att DHCPv6-klientens program kan återställa sitt DHCPv6-klient tillstånd efter, till exempel en avstängning och omstart.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klienten

- **record_ptr** Pekare till DHCPv6-klient post

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS (0x0)** En giltig klient post har skapats

- **NX_DHCPV6_NOT_BOUND** -klienten (0xE94) är inte i ett begränsat tillstånd och har därför inte tilldelats någon giltig IP-adress

- **NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Återställa DHCPv6-klient tillstånd från sparad post

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör det möjligt för ett DHCPv6-program att återskapa sitt DHCPv6-klient tillstånd från en tidigare session genom att uppdatera DHCPv6-klienten med DHCPv6-klient posten som record_ptr, och uppdaterar den tid som återstår på DHCPv6-klient lånet med time_elapsed indata. Detta gör att DHCPv6-klient programmet återskapar sin DHCPv6-klient, till exempel efter en avstängning. Detta kräver att DHCPv6-klient programmet har skapat en post för DHCPv6-klienten innan den stängs av och sparar posten till icke-flyktigt minne.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klienten

- **record_ptr** Pekare till DHCPv6-klient post

- **time_elapsed** Tid för att ta bort från den återstående låne tiden i posten för indata-klienten

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS (0x0)** Klient post återställd

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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