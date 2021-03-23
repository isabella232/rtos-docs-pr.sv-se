---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX-kryptografi
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX-krypto-komponenten.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1616667c5efd73229ed69bcd4e5de5f80e5826f9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826817"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX-kryptografi

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX-krypto-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX-kryptografi finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet inkluderar källfiler, inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_crypto. h**: offentlig API-huvudfil netx krypto-modul
- **nx_crypto_ *. c/h**: c/h källfiler för netx-kryptografi
- **nx_crypto_port. h**: C-huvudfilen som innehåller alla utvecklings verktyg och specifika data definitioner och strukturer.
- **NetX_Crypto_User_Guide.pdf**: PDF-Beskrivning av netx-krypto.

## <a name="netx-crypto-installation"></a>Installation av NetX-kryptografi

Hela den distribution som nämnts tidigare är tillgänglig i **crypto_libraries** Directory, som finns på rotnivå på netx Duo-lagringsplatsen.

För att kunna använda NetX-kryptering, bör hela distributionen som nämnts tidigare kopieras till samma katalog nivå där NetX har installerats. Om NetX till exempel är installerat i katalogen "\threadx\arm7\NetX", nx_crypto *.* kataloger bör kopieras till "\threadx\arm7\NetXCrypto".

För att NetX-kryptografi ska kunna användas i fristående läge ska hela distributionen som anges tidigare kopieras till programprojektet. Exempel: **crypto_libraries** Directory ska kopieras till programprojektet eller ett biblioteks projekt med **crypto_libraries** Directory ska skapas och länkas till programprojektet. 

## <a name="using-netx-crypto"></a>Använda NetX-kryptering

Det är enkelt att använda NetX-kryptering. Program koden måste i princip innehålla *nx_crypto. h*.  När *nx_crypto. h* ingår kan program koden sedan göra de netx för kryptografi funktionen som anges senare i den här hand boken.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa NetX-kryptografi. Följande är en lista över alla alternativ, där var och en beskrivs i detalj:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: det här alternativet anger att den maximala RSA-modulen förväntas i bitar. Standardvärdet är 4096 för en 4096-bitars Modulus. Andra värden kan vara 3072, 2048 eller 1024 (rekommenderas inte).
- **NX_CRYPTO_FIPS**: med det här alternativet aktive ras extra säkerhetsfunktioner som krävs för FIPS-Compliant användning. Det här alternativet är inte aktiverat för en icke-FIPS-version.
- **NX_CRYPTO_STANDALONE_ENABLE**: definierad aktiverar netx-kryptografi för användning i fristående läge (utan Azure-återställnings tider). Den här symbolen är inte definierad som standard.
