---
title: Servizi e transazioni
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9110198fa64e43c20e1e6ba0dcf158dddeac93a6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321141"
---
# <a name="services-and-transactions"></a><span data-ttu-id="69f52-102">Servizi e transazioni</span><span class="sxs-lookup"><span data-stu-id="69f52-102">Services and Transactions</span></span>
<span data-ttu-id="69f52-103">Le applicazioni Windows Communication Foundation (WCF) possono avviare una transazione dall'interno di un client e coordinare la transazione all'interno dell'operazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="69f52-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="69f52-104">I client possono avviare una transazione e richiamare varie operazioni di servizio nonché fare in modo che per queste ultime venga eseguito il commit o il rollback come unità singola.</span><span class="sxs-lookup"><span data-stu-id="69f52-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="69f52-105">È possibile attivare il comportamento della transazione nel contratto di servizio specificando un elemento <xref:System.ServiceModel.ServiceBehaviorAttribute> e impostando le proprietà <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> per operazioni di servizio che richiedono transazioni client.</span><span class="sxs-lookup"><span data-stu-id="69f52-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="69f52-106">Il parametro <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> specifica se la transazione in cui viene eseguito il metodo viene completata automaticamente nel caso in cui non venga generata alcuna eccezione non gestita.</span><span class="sxs-lookup"><span data-stu-id="69f52-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="69f52-107">Per ulteriori informazioni su questi attributi, vedere [attributi di transazione ServiceModel](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="69f52-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="69f52-108">Il lavoro eseguito nelle operazioni di servizio e curato da un gestore di risorse, ad esempio la registrazione di aggiornamenti del database, fa parte della transazione del client.</span><span class="sxs-lookup"><span data-stu-id="69f52-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="69f52-109">Nell'esempio seguente viene dimostrato l'utilizzo degli attributi <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> per controllare il comportamento della transazione dal lato del servizio.</span><span class="sxs-lookup"><span data-stu-id="69f52-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="69f52-110">È possibile abilitare le transazioni e il flusso delle transazioni configurando le associazioni client e di servizio per l'utilizzo del protocollo WS-AtomicTransaction e impostando il [\<transactionFlow elemento >](../configure-apps/file-schema/wcf/transactionflow.md) su `true`, come illustrato nell'esempio seguente configurazione.</span><span class="sxs-lookup"><span data-stu-id="69f52-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"   
          binding="netTcpBinding"   
          bindingConfiguration="netTcpBindingWSAT"   
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="69f52-111">I client possono iniziare una transazione creando un elemento <xref:System.Transactions.TransactionScope> e richiamando operazioni di servizio nell'ambito della transazione.</span><span class="sxs-lookup"><span data-stu-id="69f52-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="69f52-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69f52-112">See also</span></span>

- [<span data-ttu-id="69f52-113">Supporto transazionale in System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="69f52-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="69f52-114">Modelli di transazione</span><span class="sxs-lookup"><span data-stu-id="69f52-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="69f52-115">Flusso delle transazioni WS</span><span class="sxs-lookup"><span data-stu-id="69f52-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
