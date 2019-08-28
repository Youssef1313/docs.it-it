---
title: Esempio di UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 15799c1aaf3ed7df5f7721368dea426665dcf335
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044594"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="91248-102">Esempio di UriTemplate</span><span class="sxs-lookup"><span data-stu-id="91248-102">UriTemplate Sample</span></span>
<span data-ttu-id="91248-103">La classe <xref:System.UriTemplate> fornisce metodi per l'utilizzo di set di URI che condividono una struttura comune.</span><span class="sxs-lookup"><span data-stu-id="91248-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="91248-104">In questo esempio vengono illustrati i seguenti concetti principali relativi a `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="91248-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="91248-105">Sintassi per la creazione di modelli.</span><span class="sxs-lookup"><span data-stu-id="91248-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="91248-106">Creazione di istanze degli URI da un `UriTemplate` utilizzando <xref:System.UriTemplate.BindByName%2A> e <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="91248-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="91248-107"><xref:System.UriTemplateTable.Match%2A>, che corrisponde all'operazione inversa di `BindByName` e `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="91248-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="91248-108">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="91248-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="91248-109">Per compilare l'edizione in C# o Visual Basic .NET della soluzione, seguire le istruzioni in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91248-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="91248-110">Per eseguire l'esempio in una configurazione con un solo computer o tra computer diversi, seguire le istruzioni in [esecuzione degli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91248-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91248-111">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="91248-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="91248-112">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="91248-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="91248-113">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="91248-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91248-114">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="91248-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="91248-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="91248-115">See also</span></span>

- [<span data-ttu-id="91248-116">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="91248-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="91248-117">Dispatcher della tabella UriTemplate</span><span class="sxs-lookup"><span data-stu-id="91248-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
