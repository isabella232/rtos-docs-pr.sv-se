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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="23934-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX-kryptografi</span><span class="sxs-lookup"><span data-stu-id="23934-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="23934-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX-krypto-komponenten.</span><span class="sxs-lookup"><span data-stu-id="23934-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="23934-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="23934-105">Product Distribution</span></span>

<span data-ttu-id="23934-106">Azure återställnings tider NetX-kryptografi finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="23934-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="23934-107">Paketet inkluderar källfiler, inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="23934-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="23934-108">**nx_crypto. h**: offentlig API-huvudfil netx krypto-modul</span><span class="sxs-lookup"><span data-stu-id="23934-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="23934-109">\*\*nx_crypto_ \*. c/h\*\*: c/h källfiler för netx-kryptografi</span><span class="sxs-lookup"><span data-stu-id="23934-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="23934-110">**nx_crypto_port. h**: C-huvudfilen som innehåller alla utvecklings verktyg och specifika data definitioner och strukturer.</span><span class="sxs-lookup"><span data-stu-id="23934-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="23934-111">**NetX_Crypto_User_Guide.pdf**: PDF-Beskrivning av netx-krypto.</span><span class="sxs-lookup"><span data-stu-id="23934-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="23934-112">Installation av NetX-kryptografi</span><span class="sxs-lookup"><span data-stu-id="23934-112">NetX Crypto Installation</span></span>

<span data-ttu-id="23934-113">Hela den distribution som nämnts tidigare är tillgänglig i **crypto_libraries** Directory, som finns på rotnivå på netx Duo-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="23934-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="23934-114">För att kunna använda NetX-kryptering, bör hela distributionen som nämnts tidigare kopieras till samma katalog nivå där NetX har installerats.</span><span class="sxs-lookup"><span data-stu-id="23934-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="23934-115">Om NetX till exempel är installerat i katalogen "\threadx\arm7\NetX", nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="23934-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="23934-116">kataloger bör kopieras till "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="23934-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="23934-117">För att NetX-kryptografi ska kunna användas i fristående läge ska hela distributionen som anges tidigare kopieras till programprojektet.</span><span class="sxs-lookup"><span data-stu-id="23934-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="23934-118">Exempel: **crypto_libraries** Directory ska kopieras till programprojektet eller ett biblioteks projekt med **crypto_libraries** Directory ska skapas och länkas till programprojektet.</span><span class="sxs-lookup"><span data-stu-id="23934-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="23934-119">Använda NetX-kryptering</span><span class="sxs-lookup"><span data-stu-id="23934-119">Using NetX Crypto</span></span>

<span data-ttu-id="23934-120">Det är enkelt att använda NetX-kryptering.</span><span class="sxs-lookup"><span data-stu-id="23934-120">Using NetX Crypto is easy.</span></span> <span data-ttu-id="23934-121">Program koden måste i princip innehålla *nx_crypto. h*.</span><span class="sxs-lookup"><span data-stu-id="23934-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="23934-122">När *nx_crypto. h* ingår kan program koden sedan göra de netx för kryptografi funktionen som anges senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="23934-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="23934-123">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="23934-123">Configuration Options</span></span>

<span data-ttu-id="23934-124">Det finns flera konfigurations alternativ för att skapa NetX-kryptografi.</span><span class="sxs-lookup"><span data-stu-id="23934-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="23934-125">Följande är en lista över alla alternativ, där var och en beskrivs i detalj:</span><span class="sxs-lookup"><span data-stu-id="23934-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="23934-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: det här alternativet anger att den maximala RSA-modulen förväntas i bitar.</span><span class="sxs-lookup"><span data-stu-id="23934-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="23934-127">Standardvärdet är 4096 för en 4096-bitars Modulus.</span><span class="sxs-lookup"><span data-stu-id="23934-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="23934-128">Andra värden kan vara 3072, 2048 eller 1024 (rekommenderas inte).</span><span class="sxs-lookup"><span data-stu-id="23934-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="23934-129">**NX_CRYPTO_FIPS**: med det här alternativet aktive ras extra säkerhetsfunktioner som krävs för FIPS-Compliant användning.</span><span class="sxs-lookup"><span data-stu-id="23934-129">**NX_CRYPTO_FIPS**: Defined, this option enables extra security features required for FIPS-Compliant usage.</span></span> <span data-ttu-id="23934-130">Det här alternativet är inte aktiverat för en icke-FIPS-version.</span><span class="sxs-lookup"><span data-stu-id="23934-130">This option is not enabled for non-FIPS build.</span></span>
- <span data-ttu-id="23934-131">**NX_CRYPTO_STANDALONE_ENABLE**: definierad aktiverar netx-kryptografi för användning i fristående läge (utan Azure-återställnings tider).</span><span class="sxs-lookup"><span data-stu-id="23934-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="23934-132">Den här symbolen är inte definierad som standard.</span><span class="sxs-lookup"><span data-stu-id="23934-132">By default this symbol is not defined.</span></span>
