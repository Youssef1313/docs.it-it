---
title: Configurazione di classi di crittografia
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567342"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="758a0-102">Configurazione di classi di crittografia</span><span class="sxs-lookup"><span data-stu-id="758a0-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="758a0-103">Il Windows SDK consente agli amministratori di computer di configurare gli algoritmi di crittografia e le implementazioni degli algoritmi predefiniti che vengono utilizzati dall'.NET Framework e dalle applicazioni scritte in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="758a0-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="758a0-104">Ad esempio, un'azienda che dispone di una propria implementazione di un algoritmo crittografico può rendere tale implementazione il valore predefinito anziché l'implementazione fornita nel Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="758a0-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="758a0-105">Sebbene le applicazioni gestite che usano la crittografia possano sempre scegliere di eseguire un'associazione esplicita a una particolare implementazione, è consigliabile creare oggetti crittografici usando il sistema di configurazione della crittografia.</span><span class="sxs-lookup"><span data-stu-id="758a0-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="758a0-106">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="758a0-106">In This Section</span></span>  
 [<span data-ttu-id="758a0-107">Mapping di nomi di algoritmi a classi di crittografia</span><span class="sxs-lookup"><span data-stu-id="758a0-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="758a0-108">Viene descritto come eseguire il mapping di un nome di algoritmo a una classe di crittografia.</span><span class="sxs-lookup"><span data-stu-id="758a0-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="758a0-109">Mapping di identificatori di oggetti ad algoritmi di crittografia</span><span class="sxs-lookup"><span data-stu-id="758a0-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="758a0-110">Viene descritto come eseguire il mapping di un identificatore di oggetto a un algoritmo di crittografia.</span><span class="sxs-lookup"><span data-stu-id="758a0-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="758a0-111">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="758a0-111">Related Sections</span></span>  
 [<span data-ttu-id="758a0-112">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="758a0-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="758a0-113">Viene fornita una panoramica dei servizi di crittografia forniti dal Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="758a0-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="758a0-114">Schema delle impostazioni di crittografia</span><span class="sxs-lookup"><span data-stu-id="758a0-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="758a0-115">Vengono descritti gli elementi che eseguono il mapping dei nomi descrittivi degli algoritmi alle classi che implementano gli algoritmi di crittografia.</span><span class="sxs-lookup"><span data-stu-id="758a0-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
