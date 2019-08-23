---
title: Concorrenza
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: ab1cab4cf2c9fb8902eef321bfa7b1a610376771
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969036"
---
# <a name="concurrency"></a><span data-ttu-id="6cb40-102">Concorrenza</span><span class="sxs-lookup"><span data-stu-id="6cb40-102">Concurrency</span></span>
<span data-ttu-id="6cb40-103">L'esempio Concorrenza dimostra l'uso di <xref:System.ServiceModel.ServiceBehaviorAttribute> con l'enumerazione <xref:System.ServiceModel.ConcurrencyMode> che controlla se un'istanza di un servizio elabora i messaggi in sequenza o contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="6cb40-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="6cb40-104">L'esempio è basato sulla [Introduzione](../../../../docs/framework/wcf/samples/getting-started-sample.md), che implementa il `ICalculator` contratto di servizio.</span><span class="sxs-lookup"><span data-stu-id="6cb40-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="6cb40-105">In questo esempio viene definito un nuovo contratto, `ICalculatorConcurrency`, che eredita da `ICalculator`, fornendo due operazioni aggiuntive per ispezionare lo stato della concorrenza del servizio.</span><span class="sxs-lookup"><span data-stu-id="6cb40-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="6cb40-106">Modificando l'impostazione della concorrenza, è possibile osservare come viene modificato il comportamento quando si esegue il client.</span><span class="sxs-lookup"><span data-stu-id="6cb40-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="6cb40-107">In questo esempio, il client è un'applicazione console (.exe) e il servizio è ospitato da Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6cb40-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cb40-108">La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="6cb40-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6cb40-109">Sono disponibili tre modalità di concorrenza:</span><span class="sxs-lookup"><span data-stu-id="6cb40-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="6cb40-110">`Single`: Ogni istanza del servizio elabora un messaggio alla volta.</span><span class="sxs-lookup"><span data-stu-id="6cb40-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="6cb40-111">Si tratta della modalità di concorrenza predefinita.</span><span class="sxs-lookup"><span data-stu-id="6cb40-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="6cb40-112">`Multiple`: Ogni istanza del servizio elabora più messaggi contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="6cb40-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="6cb40-113">Per essere in grado di usare questa modalità di concorrenza, l'implementazione del servizio deve essere thread-safe.</span><span class="sxs-lookup"><span data-stu-id="6cb40-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="6cb40-114">`Reentrant`: Ogni istanza del servizio elabora un messaggio alla volta, ma accetta chiamate rientranti.</span><span class="sxs-lookup"><span data-stu-id="6cb40-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="6cb40-115">Il servizio accetta queste chiamate solo quando esegue chiamate in uscita. Il rientrante è illustrato nell'esempio [ConcurrencyMode.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) Reentrant.</span><span class="sxs-lookup"><span data-stu-id="6cb40-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="6cb40-116">L'uso della concorrenza è correlato alla modalità di istanza.</span><span class="sxs-lookup"><span data-stu-id="6cb40-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="6cb40-117">Nelle istanze di <xref:System.ServiceModel.InstanceContextMode.PerCall>, la concorrenza non è rilevante perché ogni messaggio viene elaborato da una nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="6cb40-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="6cb40-118">Nelle istanze di <xref:System.ServiceModel.InstanceContextMode.Single>, la concorrenza <xref:System.ServiceModel.ConcurrencyMode.Single> o <xref:System.ServiceModel.ConcurrencyMode.Multiple> è rilevante a seconda che la singola istanza elabori i messaggi in modo sequenziale o concorrente.</span><span class="sxs-lookup"><span data-stu-id="6cb40-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="6cb40-119">Nelle istanze di <xref:System.ServiceModel.InstanceContextMode.PerSession>, può essere rilevante qualsiasi modalità di concorrenza.</span><span class="sxs-lookup"><span data-stu-id="6cb40-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="6cb40-120">La classe del servizio specifica il comportamento della concorrenza con l'attributo `[ServiceBehavior(ConcurrencyMode=<setting>)]`, come illustrato nell'esempio di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="6cb40-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="6cb40-121">Tramite la modifica delle righe impostate come commento, è possibile provare le modalità di concorrenza `Single` e `Multiple`.</span><span class="sxs-lookup"><span data-stu-id="6cb40-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="6cb40-122">Ricordare di ricompilare il servizio dopo avere modificato la modalità di concorrenza.</span><span class="sxs-lookup"><span data-stu-id="6cb40-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="6cb40-123">Per impostazione predefinita l'esempio usa la concorrenza <xref:System.ServiceModel.ConcurrencyMode.Multiple> con istanze <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="6cb40-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="6cb40-124">Il codice client è stato modificato per usare un proxy asincrono.</span><span class="sxs-lookup"><span data-stu-id="6cb40-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="6cb40-125">Consente al client di eseguire più chiamate al servizio senza attendere una risposta tra ogni chiamata.</span><span class="sxs-lookup"><span data-stu-id="6cb40-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="6cb40-126">È possibile osservare la differenza nel comportamento della modalità di concorrenza del servizio.</span><span class="sxs-lookup"><span data-stu-id="6cb40-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="6cb40-127">Quando si esegue l'esempio, le richieste e le risposte dell'operazione vengono visualizzate nella finestra della console client.</span><span class="sxs-lookup"><span data-stu-id="6cb40-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6cb40-128">Viene visualizzata la modalità di concorrenza usata dal servizio, viene chiamata ciascuna operazione e quindi viene visualizzato il conteggio dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="6cb40-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="6cb40-129">Notare che quando la modalità di concorrenza è `Multiple`, i risultati vengono restituiti in un ordine diverso da quello con cui sono stati chiamati, perché il servizio elabora più messaggi contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="6cb40-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="6cb40-130">Tramite la modifica della modalità di concorrenza su `Single`, i risultati vengono restituiti nell'ordine con cui sono stati chiamati, perché il servizio elabora ogni messaggio in sequenza.</span><span class="sxs-lookup"><span data-stu-id="6cb40-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="6cb40-131">Premere INVIO nella finestra del client per arrestare il client.</span><span class="sxs-lookup"><span data-stu-id="6cb40-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6cb40-132">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="6cb40-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6cb40-133">Assicurarsi di avere eseguito la [procedura di installazione singola per gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cb40-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6cb40-134">Se si utilizza Svcutil. exe per generare il client proxy, assicurarsi di includere l' `/async` opzione.</span><span class="sxs-lookup"><span data-stu-id="6cb40-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="6cb40-135">Per compilare l'edizione in C# o Visual Basic .NET della soluzione, seguire le istruzioni in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cb40-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="6cb40-136">Per eseguire l'esempio in una configurazione con un solo computer o tra computer diversi, seguire le istruzioni in [esecuzione degli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cb40-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6cb40-137">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="6cb40-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6cb40-138">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="6cb40-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6cb40-139">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="6cb40-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6cb40-140">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="6cb40-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
