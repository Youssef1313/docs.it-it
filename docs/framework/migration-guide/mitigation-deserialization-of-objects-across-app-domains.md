---
title: 'Mitigazione: deserializzazione di oggetti tra domini app'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d172503cee4e3880f493c68d5789e17c64a82a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790005"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="b326e-102">Mitigazione: deserializzazione di oggetti tra domini app</span><span class="sxs-lookup"><span data-stu-id="b326e-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="b326e-103">In alcuni casi, quando in un'applicazione vengono utilizzati due o più domini applicazione con diverse basi di applicazione, il tentativo di deserializzare gli oggetti nel contesto di chiamata logico dei domini applicazione comporta la generazione di un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="b326e-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="b326e-104">Diagnostica del problema</span><span class="sxs-lookup"><span data-stu-id="b326e-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="b326e-105">Il problema si presenta con la sequenza di condizioni seguente:</span><span class="sxs-lookup"><span data-stu-id="b326e-105">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="b326e-106">In un'applicazione vengono utilizzati due o più domini applicazione con basi di applicazione diverse.</span><span class="sxs-lookup"><span data-stu-id="b326e-106">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="b326e-107">Alcuni tipi vengono aggiunti esplicitamente all'oggetto <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> chiamando un metodo come <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> o <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b326e-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b326e-108">Questi tipi non vengono contrassegnati come serializzabili e non sono archiviati nella Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b326e-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="b326e-109">Successivamente, tramite il codice in esecuzione nel dominio applicazione non predefinito viene effettuato il tentativo di lettura di un valore da un file di configurazione o di utilizzo di XML per deserializzare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="b326e-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="b326e-110">Per leggere da un file di configurazione o deserializzare l'oggetto, tramite un oggetto <xref:System.Xml.XmlReader> viene effettuato il tentativo di accesso al sistema di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b326e-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="b326e-111">Se il sistema di configurazione non è già stato inizializzato, deve completare la relativa inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="b326e-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="b326e-112">Ciò significa, ad esempio, che tramite il runtime deve essere creato un percorso stabile per un sistema di configurazione nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="b326e-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1. <span data-ttu-id="b326e-113">Vengono cercate le evidenze per il dominio applicazione non predefinito.</span><span class="sxs-lookup"><span data-stu-id="b326e-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2. <span data-ttu-id="b326e-114">Viene effettuato il tentativo di calcolo dell'evidenza per il dominio applicazione non predefinito in base a quello predefinito.</span><span class="sxs-lookup"><span data-stu-id="b326e-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3. <span data-ttu-id="b326e-115">La chiamata per ottenere l'evidenza per il dominio applicazione predefinito comporta una chiamata tra domini applicazione dal dominio applicazione non predefinito a quello predefinito.</span><span class="sxs-lookup"><span data-stu-id="b326e-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4. <span data-ttu-id="b326e-116">Come parte del contratto di dominio applicazione in .NET Framework, anche il contenuto del contesto di chiamata logico deve essere sottoposto a marshalling attraverso i limiti del dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="b326e-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="b326e-117">Poiché i tipi presenti nel contesto di chiamata logico non possono essere risolti nel dominio applicazione predefinito, viene generata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="b326e-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b326e-118">Mitigazione</span><span class="sxs-lookup"><span data-stu-id="b326e-118">Mitigation</span></span>  
 <span data-ttu-id="b326e-119">Per risolvere questo problema, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b326e-119">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="b326e-120">Individuare la chiamata a `get_Evidence` nello stack di chiamate quando viene generata l'eccezione.</span><span class="sxs-lookup"><span data-stu-id="b326e-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="b326e-121">L'eccezione può essere una qualsiasi di un subset di eccezioni, incluse <xref:System.IO.FileNotFoundException> e <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="b326e-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="b326e-122">Identificare la posizione nell'applicazione in cui nessun oggetto viene aggiunto al contesto di chiamata logico e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b326e-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b326e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b326e-123">See also</span></span>

- [<span data-ttu-id="b326e-124">Modifiche al runtime</span><span class="sxs-lookup"><span data-stu-id="b326e-124">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-5-1.md)
