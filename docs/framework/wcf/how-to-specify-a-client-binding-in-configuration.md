---
title: "Procedura: Specificare un'associazione al client nella configurazione"
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 0757dac4cdcffc7c3550432a71fe45b587327660
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990221"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="80ce8-102">Procedura: Specificare un'associazione al client nella configurazione</span><span class="sxs-lookup"><span data-stu-id="80ce8-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="80ce8-103">In questo esempio, viene creata un'applicazione console client per utilizzare un servizio calcolatrice e nella configurazione viene spiegata in modo dichiarativo l'associazione per quel client.</span><span class="sxs-lookup"><span data-stu-id="80ce8-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="80ce8-104">Il client accede al servizio `CalculatorService` che implementa l'interfaccia `ICalculator`. Sia il servizio sia il client utilizzano la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="80ce8-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="80ce8-105">Nella procedura illustrata si presuppone che il servizio calcolatrice sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="80ce8-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="80ce8-106">Per informazioni su come compilare il servizio, vedere [procedura: Specificare un'associazione al servizio nella](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configurazione.</span><span class="sxs-lookup"><span data-stu-id="80ce8-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="80ce8-107">Viene inoltre utilizzato lo [strumento ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) fornito da Windows Communication Foundation (WCF) per generare automaticamente i componenti client.</span><span class="sxs-lookup"><span data-stu-id="80ce8-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="80ce8-108">Lo strumento genera il codice e la configurazione client per l'accesso al servizio.</span><span class="sxs-lookup"><span data-stu-id="80ce8-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="80ce8-109">Il client viene compilato in due parti.</span><span class="sxs-lookup"><span data-stu-id="80ce8-109">The client is built in two parts.</span></span> <span data-ttu-id="80ce8-110">Lo strumento Svcutil.exe genera la classe `ClientCalculator` che implementa l'interfaccia `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="80ce8-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="80ce8-111">Questa applicazione client viene quindi costruita creando un'istanza di `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="80ce8-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="80ce8-112">La procedura solitamente consigliata consiste nello specificare in modo dichiarativo l'associazione e le informazioni dell'indirizzo nella configurazione anziché in modo imperativo nel codice.</span><span class="sxs-lookup"><span data-stu-id="80ce8-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="80ce8-113">In genere definire endpoint nel codice non è pratico in quanto le associazioni e gli indirizzi di un servizio distribuito sono solitamente diversi da quelli usati durante lo sviluppo del servizio.</span><span class="sxs-lookup"><span data-stu-id="80ce8-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="80ce8-114">Più in generale, se le informazioni su associazione e indirizzo non vengono incluse nel codice, tali dati possono essere modificati senza dover compilare o distribuire nuovamente l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="80ce8-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="80ce8-115">È possibile eseguire tutti i passaggi di configurazione seguenti utilizzando lo [strumento Editor di configurazione (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="80ce8-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="80ce8-116">Per la copia di origine di questo esempio, vedere l'esempio di [base](../../../docs/framework/wcf/samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="80ce8-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="80ce8-117">Specifica di un'associazione client nella configurazione</span><span class="sxs-lookup"><span data-stu-id="80ce8-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="80ce8-118">Utilizzare Svcutil.exe dalla riga di comando per generare il codice da metadati del servizio.</span><span class="sxs-lookup"><span data-stu-id="80ce8-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="80ce8-119">Il client generato contiene l'interfaccia `ICalculator` che definisce il contratto di servizio che l'implementazione del client deve soddisfare.</span><span class="sxs-lookup"><span data-stu-id="80ce8-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="80ce8-120">Il client generato contiene inoltre l'implementazione della classe `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="80ce8-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="80ce8-121">Svcutil.exe genera inoltre la configurazione per il client che utilizza la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="80ce8-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="80ce8-122">Quando si usa Visual Studio, assegnare un nome al file app. config. Si noti che le informazioni sull'indirizzo e sull'associazione non sono specificate nell'implementazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="80ce8-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="80ce8-123">Non è necessario, inoltre, scrivere codice per recuperarle dal file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="80ce8-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. <span data-ttu-id="80ce8-124">Creare un'istanza di `ClientCalculator` in un'applicazione, quindi chiamare le operazioni del servizio.</span><span class="sxs-lookup"><span data-stu-id="80ce8-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="80ce8-125">Compilare ed eseguire il client.</span><span class="sxs-lookup"><span data-stu-id="80ce8-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ce8-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="80ce8-126">See also</span></span>

- [<span data-ttu-id="80ce8-127">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="80ce8-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
