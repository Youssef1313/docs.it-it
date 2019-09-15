---
title: Servizi request/reply
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991146"
---
# <a name="request-reply-services"></a><span data-ttu-id="63d8b-102">Servizi request/reply</span><span class="sxs-lookup"><span data-stu-id="63d8b-102">Request-Reply Services</span></span>
<span data-ttu-id="63d8b-103">I servizi request/reply sono il tipo predefinito di contratto dell'operazione in Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63d8b-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="63d8b-104">I client effettuano chiamate alle operazioni del servizio e attendono una risposta dal servizio.</span><span class="sxs-lookup"><span data-stu-id="63d8b-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="63d8b-105">È possibile effettuare chiamate a un'operazione del servizio in modo sincrono o asincrono. Nel primo caso, il client si blocca finché non riceve una risposta dal servizio o la chiamata scade, mentre nel secondo caso il client esegue una chiamata all'operazione del servizio, continua a funzionare e riceve la risposta dal servizio su un altro thread.</span><span class="sxs-lookup"><span data-stu-id="63d8b-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="63d8b-106">Per creare un contratto di servizio request/reply, definirlo e applicare la classe <xref:System.ServiceModel.OperationContractAttribute> a ogni operazione, come illustrato nel codice di esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="63d8b-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="63d8b-107">Non è necessario impostare la proprietà <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> su `false` perché questo è il comportamento predefinito.</span><span class="sxs-lookup"><span data-stu-id="63d8b-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d8b-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="63d8b-108">See also</span></span>

- [<span data-ttu-id="63d8b-109">Servizi unidirezionali</span><span class="sxs-lookup"><span data-stu-id="63d8b-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="63d8b-110">Servizi duplex</span><span class="sxs-lookup"><span data-stu-id="63d8b-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
