---
title: Configurazione dei servizi WCF nel codice
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: c6bcf08511470d28e1087108d95e477683b0338b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320640"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="ed6b3-102">Configurazione dei servizi WCF nel codice</span><span class="sxs-lookup"><span data-stu-id="ed6b3-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="ed6b3-103">Windows Communication Foundation (WCF) consente agli sviluppatori di configurare i servizi usando i file di configurazione o il codice.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="ed6b3-104">I file di configurazione sono utili quando è necessario configurare un servizio dopo la relativa distribuzione.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="ed6b3-105">Quando si utilizzano i file di configurazione, un professionista IT deve solo aggiornare il file di configurazione. Non è necessario eseguire la ricompilazione.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="ed6b3-106">I file di configurazione, tuttavia, possono risultare complessi e difficili da gestire.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="ed6b3-107">Non è disponibile alcun supporto per il debug dei file di configurazione e, poiché il riferimento agli elementi di configurazione viene fatto in base ai nomi, i file di configurazione della creazione possono risultare difficili e soggetti a errori.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="ed6b3-108">WCF consente inoltre di configurare i servizi nel codice.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="ed6b3-109">Nelle versioni precedenti di WCF (4,0 e versioni precedenti) la configurazione dei servizi nel codice era facile in scenari indipendenti, la classe <xref:System.ServiceModel.ServiceHost> consentiva di configurare gli endpoint e i comportamenti prima di chiamare ServiceHost. Open.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="ed6b3-110">Negli scenari ospitati dal Web, tuttavia, non è possibile accedere direttamente alla classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="ed6b3-111">Per configurare un servizio ospitato dal Web era necessario creare un oggetto `System.ServiceModel.ServiceHostFactory` che creava l'oggetto <xref:System.ServiceModel.Activation.ServiceHostFactory> ed effettuava qualsiasi configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="ed6b3-112">A partire da .NET 4,5, WCF fornisce un modo più semplice per configurare i servizi ospitati in modalità self-hosted e Web nel codice.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="ed6b3-113">Metodo Configure</span><span class="sxs-lookup"><span data-stu-id="ed6b3-113">The Configure method</span></span>  
 <span data-ttu-id="ed6b3-114">Definire semplicemente un metodo statico pubblico denominato `Configure` con la firma seguente nella classe di implementazione del servizio:</span><span class="sxs-lookup"><span data-stu-id="ed6b3-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="ed6b3-115">Il metodo Configure accetta un'istanza dell'oggetto <xref:System.ServiceModel.ServiceConfiguration> che consente allo sviluppatore di aggiungere endpoint e comportamenti.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="ed6b3-116">Questo metodo viene chiamato da WCF prima dell'apertura dell'host del servizio.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="ed6b3-117">Una volta definito, tutte le impostazioni di configurazione del servizio specificate in un file app.config o web.config verranno ignorate.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="ed6b3-118">Nel frammento di codice riportato di seguito viene illustrato come definire il metodo `Configure` e aggiungere un endpoint del servizio, un comportamento dell'endpoint e comportamenti del servizio:</span><span class="sxs-lookup"><span data-stu-id="ed6b3-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="ed6b3-119">Per abilitare un protocollo come HTTPS per un servizio, è possibile aggiungere in modo esplicito un endpoint che utilizza il protocollo oppure aggiungere automaticamente gli endpoint chiamando ServiceConfiguration.EnableProtocol(Binding) che aggiunge un endpoint per ogni indirizzo di base compatibile con il protocollo e ogni contratto di servizio definito.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="ed6b3-120">Nel codice seguente viene illustrato come utilizzare il metodo ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="ed6b3-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="ed6b3-121">Le impostazioni nella sezione < `protocolMappings` > vengono utilizzate solo se non vengono aggiunti endpoint applicazione al <xref:System.ServiceModel.ServiceConfiguration> a livello di codice. Facoltativamente, è possibile caricare la configurazione del servizio dal file di configurazione dell'applicazione predefinito chiamando <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> e quindi modificare le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="ed6b3-122">La classe <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> consente inoltre di caricare la configurazione da una configurazione centralizzata.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="ed6b3-123">Nell'esempio di codice seguente viene illustrato come implementare questa azione:</span><span class="sxs-lookup"><span data-stu-id="ed6b3-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="ed6b3-124">Si noti che <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignora le impostazioni di < `host` > all'interno del tag < `service` > di < `system.serviceModel` >.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="ed6b3-125">Concettualmente, < `host` > riguarda la configurazione host e non la configurazione del servizio e viene caricata prima dell'esecuzione del metodo Configure.</span><span class="sxs-lookup"><span data-stu-id="ed6b3-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6b3-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ed6b3-126">See also</span></span>

- [<span data-ttu-id="ed6b3-127">Configurazione dei servizi tramite file di configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="ed6b3-128">Configurazione dei comportamenti client</span><span class="sxs-lookup"><span data-stu-id="ed6b3-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="ed6b3-129">Configurazione semplificata</span><span class="sxs-lookup"><span data-stu-id="ed6b3-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="ed6b3-130">Configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="ed6b3-131">Attivazione basata sulla configurazione in IIS e WAS</span><span class="sxs-lookup"><span data-stu-id="ed6b3-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="ed6b3-132">Supporto di configurazione e metadati</span><span class="sxs-lookup"><span data-stu-id="ed6b3-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="ed6b3-133">Configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="ed6b3-134">Procedura: Specificare un'associazione al servizio nella configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="ed6b3-135">Procedura: Creare un endpoint di servizio nella configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="ed6b3-136">Procedura: Pubblicare metadati per un servizio usando un file di configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="ed6b3-137">Procedura: Specificare un'associazione al client nella configurazione</span><span class="sxs-lookup"><span data-stu-id="ed6b3-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
