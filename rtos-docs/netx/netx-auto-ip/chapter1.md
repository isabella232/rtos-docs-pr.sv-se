---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX-AutoIP
description: Azure återställnings tider NetX AutoIP-protokollet är ett protokoll som utformats för att dynamiskt konfigurera IPv4-adresser i ett lokalt nätverk.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c26b4112814bb586e056246d68c2597d56df6085
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826850"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX-AutoIP
  
Azure återställnings tider NetX AutoIP-protokollet är ett protokoll som utformats för att dynamiskt konfigurera IPv4-adresser i ett lokalt nätverk. AutoIP är ett enkelt protokoll som använder ARP-funktioner för att utföra sin automatiska funktion för tilldelning av IP-adresser. AutoIP allokerar adresser i intervallet 169.254.1.0 till 169.254.254.255.

## <a name="autoip-requirements"></a>Krav för AutoIP

För att kunna fungera korrekt kräver NetX AutoIP-paketet att en NetX-IP-instans redan har skapats. Dessutom måste ARP vara aktiverat på samma IP-instans. NetX AutoIP-paketet har inga ytterligare krav.

## <a name="autoip-constraints"></a>AutoIP-begränsningar 

NetX AutoIP-protokollet implementerar kraven i RFC3927-standarden. Det finns dock följande begränsningar:

1. Om NetX DHCP används måste DHCP-tråden skapas med en högre prioritet än både NetX IP-instansnamnet och AutoIP-tråden.
1. NetX AutoIP tillhandahåller inte en mekanism för gamla IP-adresser som ska fortsätta användas.
1. När IP-adressen ändras ansvarar programmet för att bryta ned alla befintliga TCP-anslutningar och återupprätta dem på den nya IP-adressen.

## <a name="autoip-protocol-implementation"></a>Implementering av AutoIP-protokoll

NetX AutoIP-protokollet väljer först en slumpmässig adress inom AutoIP IPv4-adress intervall för 169.254.1.0 via 169.254.254.255. Du kan också tvinga fram en Start-IP-adress genom att tillhandahålla den ***nx_auto_ip_start*** funktionen. Detta är användbart i situationer där en AutoIP-adress har använts i en tidigare körning.

När du har valt en AutoIP-adress skickar NetX AutoIP ut en serie ARP-avsökningar för den valda adressen. En ARP-avsökning består av ett meddelande om ARP-begäran med avsändar adressen satt till 0.0.0.0 och mål adressen som angetts till önskad AutoIP-adress. En serie med dessa ARP-avsökningar skickas (det faktiska antalet bestäms av definiera NX_AUTO_IP_PROBE_NUM). Om en annan nätverksmapp svarar på den här avsökningen eller skickar en identisk avsökning för samma adress väljs en ny AutoIP-adress slumpmässigt i IPv4-adressintervallet för AutoIP och avsöknings bearbetningen upprepas.

Om NX_AUTO_IP_PROBE_NUM avsökningar skickas utan några svar utfärdar NetX AutoIP en serie ARP-meddelanden för den valda adressen. Ett ARP-meddelande består av ett meddelande om ARP-begäran med både avsändar-och mål adressen i ARP-meddelandet inställt på den valda AutoIP-adressen. En serie med ARP-meddelanden skickas, som motsvarar det definierade NX_AUTO_IP_ANNOUNCE_NUM. Om en annan nätverksmapp svarar på ett meddelande eller skickar ett identiskt meddelande för samma adress, väljs en ny AutoIP-adress slumpmässigt i AutoIP IPv4-adressintervallet och avsöknings bearbetningen börjar om.

När avsökningen och meddelandet slutförs utan några identifierade konflikter betraktas den valda AutoIP-adressen som giltig och den tillhör ande IP-instansen konfigureras med den här adressen.

## <a name="autoip-address-change"></a>Ändring av AutoIP-adress

Som nämnts tidigare ändrar NetX AutoIP IP-instansnamnet efter lyckad avsökning och meddelande bearbetning. Övervakning av det här ärendet är inte terribly viktigt. Det är dock möjligt att låta AutoIP-adressen ändras i framtiden. Potentiella orsaker är framtida AutoIP-konflikter samt DHCP-adress matchning. För att dessa potentiella situationer ska kunna bearbetas korrekt bör programmet använda följande NetX-API för att varna för alla och alla IP-adress ändringar:

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

Bearbetningen i den tillhandahållna *ip_address_change_notify* funktionen måste antingen starta om netx AutoIP-processorn eller inaktivera den om DHCP har löst IP-adressen. Exempel bearbetning finns i avsnittet om *litet exempel system* .

## <a name="autoip-rfcs"></a>AutoIP-rapporter

NetX AutoIP är kompatibel med RFC3927 och relaterade RFC: er.