---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo AutoIP
description: AutoIP-protokollet är ett protokoll som utformats för att dynamiskt konfigurera IPv4-adresser i ett lokalt nätverk. För att fungera korrekt kräver Azure RTOS NetX Duo AutoIP-paketet att en NetX IP-instans redan har skapats.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24fb514b71f7812266de23ec6d485dca9769a2bef491fc773a90f9945885f3df
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784911"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-autoip"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo AutoIP

AutoIP-protokollet är ett protokoll som utformats för att dynamiskt konfigurera IPv4-adresser i ett lokalt nätverk. AutoIP är ett enkelt protokoll som använder ARP-funktioner för att utföra sin automatiska tilldelningsfunktion för IP-adresser. AutoIP allokerar adresser i intervallet 169.254.1.0 till och med 169.254.254.255.

## <a name="autoip-requirements"></a>Krav för AutoIP

För att fungera korrekt kräver Azure RTOS NetX Duo AutoIP-paketet att en NetX IP-instans redan har skapats. Dessutom måste ARP vara aktiverat på samma IP-instans. NetX AutoIP-paketet har inga ytterligare krav.

## <a name="autoip-constraints"></a>AutoIP-begränsningar

Protokollet NetX AutoIP implementerar kraven för RFC3927-standarden. Det finns dock följande begränsningar:

1. Om NetX DHCP används måste DHCP-tråden skapas med högre prioritet än både NetX IP-instanstråden och AutoIP-tråden.

1. NetX AutoIP tillhandahåller ingen mekanism för att gamla IP-adresser ska fortsätta att användas.

1. När IP-adressen ändras ansvarar programmet för att bryta ned befintliga TCP-anslutningar och upprätta dem igen på den nya IP-adressen.

## <a name="autoip-protocol-implementation"></a>AutoIP-protokollimplementering

NetX AutoIP-protokollet väljer först en slumpmässig adress i AutoIP IPv4-adressintervallet 169.254.1.0 till och med 169.254.254.255. Alternativt kan programmet tvinga fram en start-IP-adress genom att tillhandahålla den ***till nx_auto_ip_start funktion.*** Detta är användbart i situationer där en AutoIP-adress har använts i en tidigare körning.

När en AutoIP-adress har valts skickar NetX AutoIP ut en serie ARP-avsökningar för den valda adressen. En ARP-avsökning består av ett ARP-begärandemeddelande med avsändaradressen inställd på 0.0.0.0 och måladressen inställd på önskad AutoIP-adress. En serie av dessa ARP-avsökningar skickas (det faktiska antalet bestäms av definierad NX_AUTO_IP_PROBE_NUM). Om en annan nätverksnod svarar på den här avsökningen eller skickar en identisk avsökning för samma adress väljs en ny AutoIP-adress slumpmässigt inom AutoIP IPv4-adressintervallet och avsökningsbearbetningen upprepas.

Om NX_AUTO_IP_PROBE_NUM skickas utan svar utfärdar NetX AutoIP en serie ARP-meddelanden för den valda adressen. Ett ARP-meddelande består av ett ARP-begärandemeddelande med både avsändarens och målets adress i ARP-meddelandet inställt på den valda AutoIP-adressen. En serie ARP-meddelanden skickas, som motsvarar definierar NX_AUTO_IP_ANNOUNCE_NUM. Om en annan nätverksnod svarar på ett aviseringsmeddelande eller skickar ett identiskt meddelande för samma adress väljs en ny AutoIP-adress slumpmässigt inom autoip-IPv4-adressintervallet och avsökningsbearbetningen startar om.

När avsökningen och meddelandet slutförs utan några identifierade konflikter anses den valda AutoIP-adressen vara giltig och den associerade IP-instansen konfigureras med den här adressen.

## <a name="autoip-address-change"></a>Ändring av AutoIP-adress

Som tidigare nämnts ändrar NetX AutoIP IP-instansadressen efter lyckad avsökning och meddelandebearbetning. Övervakning i det här fallet är inte särskilt viktigt. Det är dock möjligt att ändra AutoIP-adressen i framtiden. Potentiella orsaker är framtida AutoIP-adresskonflikter samt DHCP-adressmatchning. För att kunna bearbeta dessa potentiella situationer korrekt bör programmet använda följande NetX-API för att varna om alla IP-adressändringar:

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
            VOID *additional_info);
```

Bearbetningen i den angivna *ip_address_change_notify-funktionen* måste antingen starta om NetX AutoIP-processorn eller inaktivera den om DHCP senare har löst IP-adressen. Se avsnittet Litet *exempelsystem för* exempelbearbetning.

## <a name="autoip-rfcs"></a>AutoIP RFC

NetX AutoIP är kompatibelt med RFC3927 och relaterade RFC: er.