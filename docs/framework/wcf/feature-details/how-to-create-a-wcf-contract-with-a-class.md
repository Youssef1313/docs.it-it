---
title: 'Procedura: Creare un contratto di Windows Communication Foundation con una classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988749"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="b618c-102">Procedura: Creare un contratto di Windows Communication Foundation con una classe</span><span class="sxs-lookup"><span data-stu-id="b618c-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="b618c-103">Il modo migliore per creare un contratto di Windows Communication Foundation (WCF) consiste nell'usare un'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b618c-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="b618c-104">Per altre informazioni, vedere [Procedura: Definire un contratto](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)di servizio.</span><span class="sxs-lookup"><span data-stu-id="b618c-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="b618c-105">Un'alternativa, illustrata qui, consiste nel creare una classe e quindi nell'applicare l'attributo <xref:System.ServiceModel.ServiceContractAttribute> direttamente alla classe e l'attributo <xref:System.ServiceModel.OperationContractAttribute> a ognuno dei metodi nella classe che fanno parte del contratto.</span><span class="sxs-lookup"><span data-stu-id="b618c-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b618c-106">`[ServiceContract]` e `[ServiceContractAttribute]` eseguono la stessa operazione.</span><span class="sxs-lookup"><span data-stu-id="b618c-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="b618c-107">La stessa cosa è vera per `[OperationContract]` e `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="b618c-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="b618c-108">In ogni caso, il primo è la sintassi abbreviata per quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="b618c-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="b618c-109">Per ulteriori informazioni sui contratti di servizio, vedere [progettazione di contratti di servizio](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b618c-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="b618c-110">Creazione di un contratto Windows Communication Foundation con una classe</span><span class="sxs-lookup"><span data-stu-id="b618c-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="b618c-111">Creare una nuova classe utilizzando Visual Basic, C#o qualsiasi altra lingua del Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="b618c-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="b618c-112">Applicare la classe <xref:System.ServiceModel.ServiceContractAttribute> alla classe.</span><span class="sxs-lookup"><span data-stu-id="b618c-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="b618c-113">Creare metodi nella classe.</span><span class="sxs-lookup"><span data-stu-id="b618c-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="b618c-114">Applicare la <xref:System.ServiceModel.OperationContractAttribute> classe a ogni metodo che deve essere esposto come parte del contratto WCF pubblico.</span><span class="sxs-lookup"><span data-stu-id="b618c-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b618c-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="b618c-115">Example</span></span>  
 <span data-ttu-id="b618c-116">Nell'esempio di codice seguente viene illustrata una classe che definisce un contratto di servizio.</span><span class="sxs-lookup"><span data-stu-id="b618c-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="b618c-117">I metodi a cui è applicata la classe <xref:System.ServiceModel.OperationContractAttribute> usano per impostazione predefinita un modello di messaggio request/reply.</span><span class="sxs-lookup"><span data-stu-id="b618c-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="b618c-118">Per ulteriori informazioni su questo modello di messaggio, [vedere Procedura: Creare un contratto](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)Request/Reply.</span><span class="sxs-lookup"><span data-stu-id="b618c-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="b618c-119">È anche possibile creare e utilizzare altri modelli di messaggio impostando proprietà dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="b618c-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="b618c-120">Per altri esempi, vedere [Procedura: Creazione di un contratto](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) unidirezionale e [procedura: Creazione di un contratto](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.</span><span class="sxs-lookup"><span data-stu-id="b618c-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b618c-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b618c-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
