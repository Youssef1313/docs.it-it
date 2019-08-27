---
title: Configurazione di una channel factory
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1b74c15599ebc932a2a0ed46d646b54bec986794
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045649"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="94171-102">Configurazione di una channel factory</span><span class="sxs-lookup"><span data-stu-id="94171-102">Configuration Channel Factory</span></span>
<span data-ttu-id="94171-103">In questo esempio viene descritto l'utilizzo di <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="94171-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="94171-104">Consente <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> la gestione centralizzata della configurazione client WCF.</span><span class="sxs-lookup"><span data-stu-id="94171-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="94171-105">Può essere anche utile in scenari nei quali la configurazione viene selezionata o modificata dopo la fase di caricamento del dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="94171-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="94171-106">Dimostrazione</span><span class="sxs-lookup"><span data-stu-id="94171-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="94171-107">Discussione</span><span class="sxs-lookup"><span data-stu-id="94171-107">Discussion</span></span>
 <span data-ttu-id="94171-108">In questo esempio viene descritto come utilizzare <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> per aggiungere uno specifico file di configurazione a un'applicazione client, senza che sia necessario utilizzare il file di configurazione dell'applicazione predefinito.</span><span class="sxs-lookup"><span data-stu-id="94171-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="94171-109">L'esempio è costituito da due progetti.</span><span class="sxs-lookup"><span data-stu-id="94171-109">The sample consists of two projects.</span></span> <span data-ttu-id="94171-110">Il primo progetto è un servizio semplice in esecuzione per rispondere a messaggi provenienti dai client.</span><span class="sxs-lookup"><span data-stu-id="94171-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="94171-111">Il secondo progetto è un'applicazione client che compila due oggetti <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> utilizzando un <xref:System.Configuration.ExeConfigurationFileMap> per il file di configurazione Test.config e li utilizza per comunicare con il servizio.</span><span class="sxs-lookup"><span data-stu-id="94171-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="94171-112">Entrambi i client comunicano con il servizio utilizzando la configurazione specificata in Test.config.</span><span class="sxs-lookup"><span data-stu-id="94171-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="94171-113">Il codice seguente aggiunge un file di configurazione personalizzato a un'applicazione client.</span><span class="sxs-lookup"><span data-stu-id="94171-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94171-114">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="94171-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="94171-115">Aprire Visual Studio 2012 con privilegi di amministratore.</span><span class="sxs-lookup"><span data-stu-id="94171-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="94171-116">Fare clic con il pulsante destro del mouse sulla soluzione ConfigurationChannelFactory (2 progetti), quindi scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="94171-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="94171-117">In **Proprietà comuni**selezionare **progetto di avvio**, quindi fare clic su **progetti di avvio multipli**.</span><span class="sxs-lookup"><span data-stu-id="94171-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="94171-118">Spostare il progetto di **servizio** all'inizio dell'elenco, con l' **azione ' Avvia '** , quindi spostare il progetto **client** dopo il progetto di **servizio** , anche con l' **azione ' Avvia '** , in modo che il progetto **client** venga eseguito dopo il progetto di **servizio** .</span><span class="sxs-lookup"><span data-stu-id="94171-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="94171-119">Fare clic su **OK**, quindi premere F5 (o CTRL + F5) per eseguire l'esempio.</span><span class="sxs-lookup"><span data-stu-id="94171-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94171-120">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="94171-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94171-121">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="94171-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="94171-122">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="94171-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94171-123">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="94171-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
