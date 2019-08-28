---
title: creazione di istanze
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1e755a28ff4ce6450db4189783fa688002ebe8eb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045563"
---
# <a name="instancing"></a><span data-ttu-id="8ae15-102">creazione di istanze</span><span class="sxs-lookup"><span data-stu-id="8ae15-102">Instancing</span></span>
<span data-ttu-id="8ae15-103">Nell'esempio relativo alle istanze viene descritta l'impostazione del comportamento delle istanze che controlla come vengono create le istanze di una classe del servizio in risposta alle richieste del client.</span><span class="sxs-lookup"><span data-stu-id="8ae15-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="8ae15-104">L'esempio è basato sulla [Introduzione](../../../../docs/framework/wcf/samples/getting-started-sample.md), che implementa il `ICalculator` contratto di servizio.</span><span class="sxs-lookup"><span data-stu-id="8ae15-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="8ae15-105">Questo esempio definisce un contratto nuovo, `ICalculatorInstance`, che eredita da `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="8ae15-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="8ae15-106">Il contratto specificato da `ICalculatorInstance` fornisce tre operazioni aggiuntive per il controllo dello stato dell'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="8ae15-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="8ae15-107">Modificando l'impostazione delle istanze, è possibile osservare come viene modificato il comportamento quando si esegue il client.</span><span class="sxs-lookup"><span data-stu-id="8ae15-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="8ae15-108">In questo esempio, il client è un'applicazione console (.exe) e il servizio è ospitato da Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="8ae15-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ae15-109">La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="8ae15-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8ae15-110">Sono disponibili le modalità di istanza seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ae15-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="8ae15-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Viene creata una nuova istanza del servizio per ogni richiesta del client.</span><span class="sxs-lookup"><span data-stu-id="8ae15-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="8ae15-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Viene creata una nuova istanza per ogni nuova sessione client e mantenuta per la durata di tale sessione (è necessaria un'associazione che supporti la sessione).</span><span class="sxs-lookup"><span data-stu-id="8ae15-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="8ae15-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Una singola istanza della classe Service gestisce tutte le richieste client per la durata dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8ae15-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="8ae15-114">La classe del servizio specifica il comportamento di istanza con l'attributo `[ServiceBehavior(InstanceContextMode=<setting>)]`, come illustrato nell'esempio di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="8ae15-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="8ae15-115">Modificando quali righe vengono impostate come commento, è possibile osservare il comportamento di ognuna delle modalità dell'istanza.</span><span class="sxs-lookup"><span data-stu-id="8ae15-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="8ae15-116">Ricordarsi di ricompilare il servizio dopo avere modificato la modalità dell'istanza.</span><span class="sxs-lookup"><span data-stu-id="8ae15-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="8ae15-117">Non è necessario specificare impostazioni correlate all'istanza sul client.</span><span class="sxs-lookup"><span data-stu-id="8ae15-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="8ae15-118">Quando si esegue l'esempio, le richieste e le risposte dell'operazione vengono visualizzate nella finestra della console client.</span><span class="sxs-lookup"><span data-stu-id="8ae15-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8ae15-119">Viene visualizzata la modalità dell'istanza nel quale viene eseguito il servizio.</span><span class="sxs-lookup"><span data-stu-id="8ae15-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="8ae15-120">Dopo ogni operazione, l'ID dell'istanza e il conteggio dell'operazione vengono visualizzati per riflettere il comportamento della modalità dell'istanza.</span><span class="sxs-lookup"><span data-stu-id="8ae15-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="8ae15-121">Premere INVIO nella finestra del client per arrestare il client.</span><span class="sxs-lookup"><span data-stu-id="8ae15-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ae15-122">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="8ae15-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8ae15-123">Assicurarsi di avere eseguito la [procedura di installazione singola per gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ae15-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8ae15-124">Per compilare l'edizione in C# o Visual Basic .NET della soluzione, seguire le istruzioni in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ae15-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8ae15-125">Per eseguire l'esempio in una configurazione con un solo computer o tra computer diversi, seguire le istruzioni in [esecuzione degli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ae15-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8ae15-126">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="8ae15-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8ae15-127">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="8ae15-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8ae15-128">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="8ae15-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ae15-129">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="8ae15-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
