---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo SNMP-agenten
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo SNMP agent-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f011b73217c7f413dd19c555e9c2d40dace305ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825764"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo SNMP-agenten

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo SNMP agent-komponenten.

## <a name="product-distribution"></a>Produkt distribution

SNMP-agenten för NetX Duo finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller fyra källfiler, en include-fil och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_snmp. h** Rubrik fil för SNMP för NetX Duo
- **demo_snmp_helper. h** Rubrik fil för SNMP MIB-data
- **nxd_snmp. c** C-källfil för SNMP-agent för NetX Duo
- **nx_md5. c** MD5 Digest-algoritmer
- **nx_sha. c** SHA Digest-algoritmer
- **nx_des. c** Algoritmer för DES-kryptering
- **nxd_snmp.pdf** Användar handbok för SNMP-agenten för NetX Duo
- **demo_netxduo_snmp. c** Enkel SNMP-demonstration
- **demo_netxduo_mib2. c** Enkel MIB2-demonstration (MIB har IPv6-adress element)
- **demo_snmp_helper. h** Rubrik fil som definierar MIB-element

## <a name="netx-duo-snmp-agent-installation"></a>Installation av NetX Duo SNMP-agent

För att kunna använda NetX Duo SNMP bör hela den distribution som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat. Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*" måste du kopiera *nxd_snmp. h*-, *nxd_snmp. c*-, *nx_md5. c-, nx_sha. c* -och nx_ *des. c* -filer till den här katalogen.

## <a name="using-the-netx-duo-snmp-agent"></a>Använda NetX Duo SNMP-agenten

Programmet måste ha *nxd_snmp. c*, *nx_md5. c, nx_sha. c* och *nx_des. c* i build-projektet. Program koden måste också innehålla *nxd_snmp. h* när den innehåller *nx_api. h för* att kunna anropa SNMP-tjänster. Filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade till NetX Duo-biblioteket. Detta är allt som krävs för att använda NetX Duo SNMP.

> [!NOTE]
> *Om **NX_SNMP_NO_SECURITY** anges i build-processen behövs inte filerna nx_md5. c, nx_sha. c och nx_des. c.*

> [!NOTE]
> Eftersom NetX Duo SNMP använder UDP-tjänster måste UDP aktive ras med det *nx_udp_enable* anropet innan SNMP används.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur du använder NetX Duo SNMP-agenten beskrivs i bild 1,0 som visas nedan. I det här exemplet tas SNMP-filen *nxd_snmp. h* in på rad 6. Rubrik filen som definierar MIB-databasens element, *demo_snmp_helper. h,* tas i rad 8. MIB: en definieras med början på rad 32. Därefter skapas SNMP-agenten i "*tx_application_define*" på rad 129. Observera att SNMP agent Control Block "*my_agent*" definierades som en global variabel på rad 18 tidigare. Om IPv6 är aktiverat registreras IPv6-adresserna med IP-instansen på raderna 166-223. SNMP-agenten startas på rad 229. Objekt för återanrop av SNMP-objekt för SNMP-hanteraren GET-, GETNEXT-och SET-förfrågningar, samt användar namn och MIB-begäranden, bearbetas med början på rad 250. I det här exemplet utförs ingen autentisering.

> [!NOTE]
> *MIB2-tabellen som visas nedan är bara ett exempel. Programmet kan använda en annan MIB och inkludera den i separata filer, samt definiera GET-, GETNEXT-eller SET-bearbetning enligt deras program krav.*

```c
/* This is a small demo of the NetX SNMP Agent on the high-performance NetX TCP/IP  
   stack. This demo relies on ThreadX and NetX to show simple SNMP the SNMP
   GET/GETNEXT/SET requests on MIB-2 objects.  */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_snmp.h"
#include  "demo_snmp_helper.h"

#define     DEMO_STACK_SIZE         4096
#define     AGENT_PRIMARY_ADDRESS   IP_ADDRESS(192, 2, 2, 66)

/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_SNMP_AGENT           my_agent;


/* Indicate if using IPv6 to communicate with SNMP servers. Note that
   IPv6 must be enabled in the NetX Duo library first. Further, IPv6
   and ICMPv6 services are enabled before starting the SNMP agent. */
#define USE_IPV6


/* Define authentication and privacy keys.  */

#ifdef AUTHENTICATION_REQUIRED
NX_SNMP_SECURITY_KEY    my_authentication_key;
#endif

#ifdef PRIVACY_REQUIRED
NX_SNMP_SECURITY_KEY    my_privacy_key;
#endif

/* Define an error counter variable. */
UINT error_counter = 0;

/* This binds a secondary interfaces to the primary IP network interface 
   if SNMP is required for required for that interface. */
/* #define  MULTI_HOMED_DEVICE */

/* Define function prototypes.  A generic ram driver is used in this demo.  However
   to properly run an SNMP agent demo, a real driver should be substituted. */

VOID    thread_agent_entry(ULONG thread_input);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username);
VOID    mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr);


UCHAR context_engine_id[] = {0x80, 0x00, 0x0d, 0xfe, 0x03, 0x00, 0x11, 0x23, 0x23, 
                             0x44, 0x55};
UINT  context_engine_size = 11;
UCHAR context_name[] = {0x69, 0x6e, 0x69, 0x74, 0x69, 0x61, 0x6c};
UINT  context_name_size = 7;

/* Define main entry point.  */

int main()
{

   /* Enter the ThreadX kernel.  */
   tx_kernel_enter();
}


/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UCHAR   *pointer;
UINT    status;


   /* Setup the working pointer.  */
   pointer =  (UCHAR *) first_unused_memory;

   status = tx_thread_create(&thread_0, "agent thread", thread_agent_entry, 0,  
            pointer, DEMO_STACK_SIZE, 
            4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
   if (status != NX_SUCCESS)
   {
      return;
   }

   pointer =  pointer + DEMO_STACK_SIZE;


   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create packet pool.  */
   status = nx_packet_pool_create(&pool_0, "NetX Packet Pool 0", 2048, 
                                   pointer, 20000);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer = pointer + 20000;
  
   /* Create an IP instance.  */
   status = nx_ip_create(&ip_0, "SNMP Agent IP Instance", AGENT_PRIMARY_ADDRESS, 
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
   nx_arp_enable(&ip_0, (void *) pointer, 1024);
   pointer = pointer + 1024;

   /* Enable UPD processing for IP instance.  */
   nx_udp_enable(&ip_0);
  
   /* Enable ICMP for ping.  */
   nx_icmp_enable(&ip_0);
  
   /* Create an SNMP agent instance.  */
   status = nx_snmp_agent_create(&my_agent, "SNMP Agent", &ip_0, pointer, 4096, 
                                 &pool_0, 
                                 mib2_username_processing, mib2_get_processing, 
                                 mib2_getnext_processing, 
                                 mib2_set_processing);


  
   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   status = nx_snmp_agent_context_engine_set(&my_agent, context_engine_id, 
                                             context_engine_size);
  
   if (status != NX_SUCCESS)
   {
      error_counter++;
   }
  
   return;
}
  
VOID thread_agent_entry(ULONG thread_input)
{
  
#ifdef USE_IPV6
UINT        iface_index, address_index;
UINT        status;
NXD_ADDRESS agent_ipv6_address;
#endif
  
  
      /* Allow NetX time to get initialized. */
      tx_thread_sleep(100);
  
      /* If using IPv6, enable IPv6 and ICMPv6 services and get IPv6 addresses 
         registered with NetX Dou. */
  
#ifdef USE_IPV6
  
      /* Enable IPv6 on the IP instance. */
      status = nxd_ipv6_enable(&ip_0);
   
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
      /* Enable ICMPv6 on the IP instance. */
      status = nxd_icmp_enable(&ip_0);
  
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
  
      agent_ipv6_address.nxd_ip_address.v6[3] = 0x101;
      agent_ipv6_address.nxd_ip_address.v6[2] = 0x0;
      agent_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
      agent_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
      agent_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
  
      /* Set the primary interface for our DNS IPv6 addresses. */
      iface_index = 0;
  
      /* This assumes we are using the primary network interface (index 0). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, NX_NULL, 10, &address_index);
  
      /* Check for link local address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }
  
      /* Set the host global IP address. We are assuming a 64 
         bit prefix here but this can be any value (< 128). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, &agent_ipv6_address, 64, 
                                    &address_index);
  
      /* Check for global address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }

      /* Wait while NetX Duo validates the link local and global address. */
      tx_thread_sleep(500);
#endif
  
#ifdef AUTHENTICATION_REQUIRED

      /* Create an authentication key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "authpassword", &my_authentication_key);
  
      /* Use the authentication key.  */
      nx_snmp_agent_authenticate_key_use(&my_agent, &my_authentication_key);
#endif
  
#ifdef PRIVACY_REQUIRED
  
      /* Create a privacy key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "privpassword", &my_privacy_key);
  
      /* Use the privacy key.  */
      nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);
#endif
  
      /* Start the SNMP instance.  */
      nx_snmp_agent_start(&my_agent);
  
}
  
/* Define the application's GET processing routine.  */
  
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
      printf("SNMP Manager GET Request For:  %s", object_requested);
  
      /* Loop through the sample MIB to see if we have information for the supplied 
         variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's GETNEXT processing routine.  */
  
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                                NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager GETNEXT Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied 
      variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the next entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Is the next entry the mib greater?  */
         if (status == NX_SNMP_NEXT_ENTRY)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SNMP_NEXT_ENTRY)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Copy the new name into the object.  */
      nx_snmp_object_copy(mib2_mib[i].object_name, object_requested);
  
      printf(" Next Name is: %s", object_requested);
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
  
         /* Determine if the object data indicates an end-of-mib condition.  */
         if (object_data -> nx_snmp_object_data_type == NX_SNMP_END_OF_MIB_VIEW)
         {
  
            /* Copy the name supplied in the mib table.  */
            nx_snmp_object_copy(mib2_mib[i].object_value_ptr, object_requested);
         }
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's SET processing routine.  */
  
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager SET Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Determine if the entry has a set function.  */
      if (mib2_mib[i].object_set_callback)
      {
  
         /* Yes, call the set function.  */
         status =  (mib2_mib[i].object_set_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO SET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's authentication routine.  */
  
UINT  mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username)
{
  
      printf("Username is:  %s\n", username);
  
      /* Update MIB-2 objects. In this example, it is only the SNMP objects.  */
      mib2_variable_update(&ip_0, &my_agent);
  
      /* No authentication is done, just return success!  */
      return(NX_SUCCESS);
}
  
  
/* Define the application's update routine.  */ 
  
VOID  mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr)
{
  
      /* Update the snmp parameters.  */
      snmpInPkts =                agent_ptr -> nx_snmp_agent_packets_received;
      snmpOutPkts =               agent_ptr -> nx_snmp_agent_packets_sent;
      snmpInBadVersions =         agent_ptr -> nx_snmp_agent_invalid_version;
      snmpInBadCommunityNames =   agent_ptr -> nx_snmp_agent_authentication_errors;
      snmpInBadCommunityUsers =   agent_ptr -> nx_snmp_agent_username_errors; 
      snmpInASNParseErrs =        agent_ptr -> nx_snmp_agent_internal_errors;
      snmpInTotalReqVars =        agent_ptr -> nx_snmp_agent_total_get_variables;
      snmpInTotalSetVars =        agent_ptr -> nx_snmp_agent_total_set_variables;
      snmpInGetRequests =         agent_ptr -> nx_snmp_agent_get_requests;
      snmpInGetNexts =            agent_ptr -> nx_snmp_agent_getnext_requests;
      snmpInSetRequests =         agent_ptr -> nx_snmp_agent_set_requests;
      snmpOutTooBigs =            agent_ptr -> nx_snmp_agent_too_big_errors;
      snmpOutNoSuchNames =        agent_ptr -> nx_snmp_agent_no_such_name_errors;
      snmpOutBadValues =          agent_ptr -> nx_snmp_agent_bad_value_errors;
      snmpOutGenErrs =            agent_ptr -> nx_snmp_agent_general_errors;
      snmpOutTraps =              agent_ptr -> nx_snmp_agent_traps_sent;
}   
```
Figur 1,0 exempel på SNMP-agent användning med NetX Duo

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa SNMP för NetX Duo. Följande är en lista över alla alternativ, där var och en beskrivs i detalj:  
  
| Definierar                     | Innebörd                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **NX_SNMP_AGENT_PRIORITY**     | Trådens prioritet för SNMP-AGENTen. Som standard definieras värdet som 16 för att ange prioritet 16.                                                                                                                                                                         |
| **NX_SNMP_TYPE_OF_SERVICE**    | Typ av tjänst som krävs för SNMP UDP-svar. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering. Den här inställningen kan anges av programmet innan *nxd_snmp. h.*                                                       |
| **NX_SNMP_FRAGMENT_OPTION**    | Fragment aktivera för SNMP UDP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera SNMP UDP-fragmentering. Den här inställningen kan anges av programmet innan *nxd_snmp. h.*                                                                                 |
| **NX_SNMP_TIME_TO_LIVE**       | Anger TTL-tiden innan den upphör att gälla. Standardvärdet är inställt på 0x80, men kan omdefinieras innan du tar med *nxd_snmp. h.*                                                                                                                                         |
| **NX_SNMP_AGENT_TIMEOUT**      | Anger antalet ThreadX-Tick som interna tjänster ska pausas för. Standardvärdet är inställt på 100, men kan omdefinieras innan *nxd_snmp. h.*                                                                                                         |
| **NX_SNMP_MAX_OCTET_STRING**   | Anger det maximala antalet byte som tillåts i en oktett-sträng i SNMP-agenten. Standardvärdet är inställt på 255, men kan omdefinieras innan *nxd_snmp. h.*                                                                                                    |
| **NX_SNMP_MAX_CONTEXT_STRING** | Anger det maximala antalet byte för en kontext motor sträng i SNMP-agenten. Standardvärdet är inställt på 32, men kan omdefinieras innan *nxd_snmp. h.*                                                                                                    |
| **NX_SNMP_MAX_USER_NAME**      | Anger maximalt antal byte i ett användar namn (inklusive grupp strängar). Standardvärdet är inställt på 64, men kan omdefinieras innan *nxd_snmp. h.*                                                                                                      |
| **NX_SNMP_MAX_SECURITY_KEY**   | Anger antalet byte som tillåts i en säkerhets nyckel sträng. Standardvärdet är inställt på 64, men kan definieras om före nclusion av *nxd_snmp. h.*                                                                                                                          |
| **NX_SNMP_PACKET_SIZE**        | Anger minimi storleken på paketen i poolen som anges vid skapande av SNMP-agent. Minimi storleken krävs för att säkerställa att den fullständiga SNMP-nyttolasten kan finnas i ett paket. Standardvärdet är inställt på 560, men kan omdefinieras innan *nxd_snmp. h.* |
| **NX_SNMP_AGENT_PORT**         | Anger UDP-porten till fältet SNMP Manager-begäranden på. Standard porten är UDP-port 161, men den kan definieras om innan du kan inkludera *nxd_snmp. h.*                                                                                                                             |
| **NX_SNMP_MANAGER_TRAP_PORT**  | Anger UDP-porten som SNMP-agentens trap-begär Anden ska skickas till. Standard porten är UDP-port 162, men den kan definieras om innan du kan inkludera *nxd_snmp. h.*                                                                                                                           |
| **NX_SNMP_MAX_TRAP_NAME**      | Anger storleken på den matris som ska innehålla användar namnet som skickas med trap-meddelanden. Standardvärdet är 64.                                                                                                                                                                         |
| **NX_SNMP_MAX_TRAP_KEY**       | Anger storleken på autentiserings-och sekretess nycklar för trap-meddelanden. Standardvärdet är 64.                                                                                                                                                                          |
| **NX_SNMP_TIME_INTERVAL**      | Detta avgör ström spar intervallet i timer-Tick som tas av aktiviteten SNMP-tråd mellan att bearbeta mottagna SNMP-paket. Standardvärdet är 100. Under det här ström spar intervallet har värd programmet åtkomst till SNMP API-tjänster.                                           |
| **NX_SNMP_DISABLE_V1**         | Definierad tar detta bort all bearbetning av SNMP version 1 i *nxd_snmp. c.* Som standard är detta inte definierat.                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V2**         | Definierad tar detta bort all bearbetning av SNMP version 2 i *nxd_snmp. c.* Som standard är detta inte definierat.                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V3**         | Definierad tar detta bort all SNMPv3-bearbetning i *nxd_snmp. c.* Som standard är detta inte definierat.                                                                                                                                                                                 |