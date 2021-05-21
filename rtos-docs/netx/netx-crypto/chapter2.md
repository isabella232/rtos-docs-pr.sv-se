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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="da4ba-103">Kapitel 2 – Installation och användning av Azure RTOS NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="da4ba-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="da4ba-104">Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Crypto-komponenten.</span><span class="sxs-lookup"><span data-stu-id="da4ba-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="da4ba-105">Produktdistribution</span><span class="sxs-lookup"><span data-stu-id="da4ba-105">Product Distribution</span></span>

<span data-ttu-id="da4ba-106">Azure RTOS NetX Crypto finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="da4ba-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="da4ba-107">Paketet innehåller källfiler, inklusive filer och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="da4ba-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="da4ba-108">**nx_crypto.h:** Offentlig API-huvudfil NetX Crypto-modul</span><span class="sxs-lookup"><span data-stu-id="da4ba-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="da4ba-109">**nx_crypto_\*.c/h:** C/H-källfiler för NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="da4ba-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="da4ba-110">**nx_crypto_port.h:** C-huvudfil som innehåller alla utvecklingsverktyget och målspecifika datadefinitioner och strukturer.</span><span class="sxs-lookup"><span data-stu-id="da4ba-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="da4ba-111">**NetX_Crypto_User_Guide.pdf:** PDF-beskrivning av NetX Crypto Module.</span><span class="sxs-lookup"><span data-stu-id="da4ba-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="da4ba-112">NetX Crypto-installation</span><span class="sxs-lookup"><span data-stu-id="da4ba-112">NetX Crypto Installation</span></span>

<span data-ttu-id="da4ba-113">Hela distributionen som nämnts tidigare är **tillgänglig crypto_libraries** katalog, som finns på rotnivå för NetX Duo-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="da4ba-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="da4ba-114">För att kunna använda NetX Crypto bör hela distributionen som nämns ovan kopieras till samma katalognivå där NetX är installerat.</span><span class="sxs-lookup"><span data-stu-id="da4ba-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="da4ba-115">Om NetX till exempel är installerat i katalogen "\threadx\arm7\NetX" nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="da4ba-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="da4ba-116">-katalogerna ska kopieras till "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="da4ba-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="da4ba-117">För att NetX Crypto ska användas i fristående läge ska hela distributionen som nämns ovan kopieras till programprojektet.</span><span class="sxs-lookup"><span data-stu-id="da4ba-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="da4ba-118">Till exempel **crypto_libraries** katalog kopieras till programprojektet eller ett biblioteksprojekt **med crypto_libraries** ska skapas och länkas till programprojektet.</span><span class="sxs-lookup"><span data-stu-id="da4ba-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="da4ba-119">Använda NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="da4ba-119">Using NetX Crypto</span></span>

<span data-ttu-id="da4ba-120">I det här kapitlet beskrivs installation, installation och användning av Azure RTOS NetX Crypto-komponenten.</span><span class="sxs-lookup"><span data-stu-id="da4ba-120">This chapter describes installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span> <span data-ttu-id="da4ba-121">I princip måste programkoden innehålla *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="da4ba-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="da4ba-122">När *nx_crypto.h* ingår kan programkoden sedan göra de NetX Crypto-funktionsanrop som anges senare i den här guiden.</span><span class="sxs-lookup"><span data-stu-id="da4ba-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="da4ba-123">Konfigurationsalternativ</span><span class="sxs-lookup"><span data-stu-id="da4ba-123">Configuration Options</span></span>

<span data-ttu-id="da4ba-124">Det finns flera konfigurationsalternativ för att skapa NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="da4ba-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="da4ba-125">Följande är en lista över alla alternativ, där vart och ett beskrivs i detalj:</span><span class="sxs-lookup"><span data-stu-id="da4ba-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="da4ba-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE:** Det här alternativet ger maximalt antal RSA-modulus som förväntas, i bitar.</span><span class="sxs-lookup"><span data-stu-id="da4ba-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="da4ba-127">Standardvärdet är 4096 för en 4096-bitars modulus.</span><span class="sxs-lookup"><span data-stu-id="da4ba-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="da4ba-128">Andra värden kan vara 3072, 2048 eller 1024 (rekommenderas inte).</span><span class="sxs-lookup"><span data-stu-id="da4ba-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="da4ba-129">**NX_CRYPTO_SELF_TEST:** Definierad aktiverar självtester för NetX Crypto-modulen.</span><span class="sxs-lookup"><span data-stu-id="da4ba-129">**NX_CRYPTO_SELF_TEST**: Defined, enables self tests for NetX Crypto module.</span></span> <span data-ttu-id="da4ba-130">**NX_CRYPTO_FIPS** är nu inaktuell och har bytt namn till **NX_CRYPTO_SELF_TEST**</span><span class="sxs-lookup"><span data-stu-id="da4ba-130">**NX_CRYPTO_FIPS** symbol is now deprecated and renamed to **NX_CRYPTO_SELF_TEST**</span></span>
- <span data-ttu-id="da4ba-131">**NX_CRYPTO_STANDALONE_ENABLE:** Definierad gör att NetX Crypto kan användas i fristående läge (utan Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="da4ba-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="da4ba-132">Som standard definieras inte den här symbolen.</span><span class="sxs-lookup"><span data-stu-id="da4ba-132">By default this symbol is not defined.</span></span>
