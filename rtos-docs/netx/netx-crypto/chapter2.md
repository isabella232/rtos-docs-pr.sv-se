---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Crypto
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Crypto-komponenten.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd736cf6bbe15e1f407d1812072a4308435c8007
ms.sourcegitcommit: c2f5da5d6c7b230799f8fbd77885e9940acfbab4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/21/2021
ms.locfileid: "110236160"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Crypto

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Crypto-komponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX Crypto finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller källfiler, inklusive filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_crypto.h:** Offentlig API-huvudfil NetX Crypto-modul
- **nx_crypto_*.c/h:** C/H-källfiler för NetX Crypto
- **nx_crypto_port.h:** C-huvudfil som innehåller alla utvecklingsverktyget och målspecifika datadefinitioner och strukturer.
- **NetX_Crypto_User_Guide.pdf:** PDF-beskrivning av NetX Crypto Module.

## <a name="netx-crypto-installation"></a>NetX Crypto-installation

Hela distributionen som nämnts tidigare är **tillgänglig crypto_libraries** katalog, som finns på rotnivå för NetX Duo-lagringsplatsen.

För att kunna använda NetX Crypto bör hela distributionen som nämns ovan kopieras till samma katalognivå där NetX är installerat. Om NetX till exempel är installerat i katalogen "\threadx\arm7\NetX" nx_crypto *.* -katalogerna ska kopieras till "\threadx\arm7\NetXCrypto".

För att NetX Crypto ska användas i fristående läge ska hela distributionen som nämns ovan kopieras till programprojektet. Till exempel **crypto_libraries** katalog kopieras till programprojektet eller ett biblioteksprojekt **med crypto_libraries** ska skapas och länkas till programprojektet. 

## <a name="using-netx-crypto"></a>Använda NetX Crypto

I det här kapitlet beskrivs installation, installation och användning av Azure RTOS NetX Crypto-komponenten. I princip måste programkoden innehålla *nx_crypto.h*.  När *nx_crypto.h* ingår kan programkoden sedan göra de NetX Crypto-funktionsanrop som anges senare i den här guiden.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa NetX Crypto. Följande är en lista över alla alternativ, där vart och ett beskrivs i detalj:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE:** Det här alternativet ger maximalt antal RSA-modulus som förväntas, i bitar. Standardvärdet är 4096 för en 4096-bitars modulus. Andra värden kan vara 3072, 2048 eller 1024 (rekommenderas inte).
- **NX_CRYPTO_SELF_TEST:** Definierad aktiverar självtester för NetX Crypto-modulen. **NX_CRYPTO_FIPS** är nu inaktuell och har bytt namn till **NX_CRYPTO_SELF_TEST**
- **NX_CRYPTO_STANDALONE_ENABLE:** Definierad gör att NetX Crypto kan användas i fristående läge (utan Azure RTOS). Som standard definieras inte den här symbolen.
