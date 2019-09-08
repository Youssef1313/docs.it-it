---
title: 'Procedura: Ispezionare o modificare i messaggi sul client'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 14c24c16a36be600881de402de50086dd18b30b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796976"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="7ff38-102">Procedura: Ispezionare o modificare i messaggi sul client</span><span class="sxs-lookup"><span data-stu-id="7ff38-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="7ff38-103">È possibile ispezionare o modificare i messaggi in ingresso o in uscita in un client WCF implementando <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> un e inserendolo nel runtime del client.</span><span class="sxs-lookup"><span data-stu-id="7ff38-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="7ff38-104">Per ulteriori informazioni, vedere [estensione dei client](extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7ff38-104">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="7ff38-105">La funzionalità equivalente nel servizio è <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ff38-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ff38-106">Per un esempio di codice completo, vedere l'esempio [Message Inspectors](../samples/message-inspectors.md) .</span><span class="sxs-lookup"><span data-stu-id="7ff38-106">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="7ff38-107">Per ispezionare o modificare i messaggi</span><span class="sxs-lookup"><span data-stu-id="7ff38-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="7ff38-108">Implementare l'interfaccia <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ff38-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="7ff38-109">Implementare <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> o <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> in base all'ambito in cui si desidera inserire il controllo dei messaggi client.</span><span class="sxs-lookup"><span data-stu-id="7ff38-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="7ff38-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>consente di modificare il comportamento a livello di endpoint.</span><span class="sxs-lookup"><span data-stu-id="7ff38-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="7ff38-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>consente di modificare il comportamento a livello di contratto.</span><span class="sxs-lookup"><span data-stu-id="7ff38-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="7ff38-112">Inserire il comportamento prima di chiamare il metodo <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> su <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ff38-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ff38-113">Per informazioni dettagliate, vedere [configurazione ed estensione del runtime con i comportamenti](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="7ff38-113">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ff38-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="7ff38-114">Example</span></span>  
 <span data-ttu-id="7ff38-115">Negli esempi di codice seguenti vengono illustrati, nell'ordine:</span><span class="sxs-lookup"><span data-stu-id="7ff38-115">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="7ff38-116">Un'implementazione del controllo client.</span><span class="sxs-lookup"><span data-stu-id="7ff38-116">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="7ff38-117">Un comportamento dell'endpoint che inserisce il controllo.</span><span class="sxs-lookup"><span data-stu-id="7ff38-117">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="7ff38-118">Una classe derivata da <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>che consente di aggiungere il comportamento in un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="7ff38-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="7ff38-119">Un file di configurazione che aggiunge il comportamento dell'endpoint che inserisce il controllo dei messaggi client nel runtime del client.</span><span class="sxs-lookup"><span data-stu-id="7ff38-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client   
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they   
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element   
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"   
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ff38-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7ff38-120">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="7ff38-121">Configurazione ed estensione del runtime con i comportamenti</span><span class="sxs-lookup"><span data-stu-id="7ff38-121">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
