---
title: 'Procedura: Proteggere un servizio con credenziali di Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 19ac9da94ce6e405632293a7d569698c9d866bef
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856054"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="208c5-102">Procedura: Proteggere un servizio con credenziali di Windows</span><span class="sxs-lookup"><span data-stu-id="208c5-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="208c5-103">In questo argomento viene illustrato come abilitare la sicurezza del trasporto in un servizio Windows Communication Foundation (WCF) che risiede in un dominio di Windows e viene chiamato dai client nello stesso dominio.</span><span class="sxs-lookup"><span data-stu-id="208c5-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="208c5-104">Per ulteriori informazioni su questo scenario, vedere [sicurezza del trasporto con l'autenticazione di Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="208c5-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="208c5-105">Per un'applicazione di esempio, vedere l'esempio [wsHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="208c5-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="208c5-106">In questo argomento si presuppone la presenza di un'interfaccia e di un'implementazione del contratto esistente già definite, alle quali vengono aggiunti elementi.</span><span class="sxs-lookup"><span data-stu-id="208c5-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="208c5-107">È inoltre possibile modificare un servizio e un client esistenti.</span><span class="sxs-lookup"><span data-stu-id="208c5-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="208c5-108">È possibile proteggere un servizio con credenziali di Windows completamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="208c5-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="208c5-109">In alternativa, è possibile omettere parte del codice tramite un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="208c5-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="208c5-110">In questo argomento vengono illustrate entrambe le modalità.</span><span class="sxs-lookup"><span data-stu-id="208c5-110">This topic shows both ways.</span></span> <span data-ttu-id="208c5-111">Accertarsi di usare una sola modalità, non entrambe.</span><span class="sxs-lookup"><span data-stu-id="208c5-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="208c5-112">Nelle prime tre procedure viene illustrato come proteggere il servizio tramite il codice.</span><span class="sxs-lookup"><span data-stu-id="208c5-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="208c5-113">Nella quarta e nella quinta procedura viene illustrato come eseguire questa operazione con un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="208c5-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="208c5-114">Uso del codice</span><span class="sxs-lookup"><span data-stu-id="208c5-114">Using Code</span></span>

<span data-ttu-id="208c5-115">Il codice completo per il servizio e il client si trova nella sezione Esempio alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="208c5-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="208c5-116">Nella prima procedura vengono illustrate la creazione e la configurazione di una classe <xref:System.ServiceModel.WSHttpBinding> nel codice.</span><span class="sxs-lookup"><span data-stu-id="208c5-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="208c5-117">Per l'associazione viene usata il trasporto HTTP.</span><span class="sxs-lookup"><span data-stu-id="208c5-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="208c5-118">La stessa associazione viene usata nel client.</span><span class="sxs-lookup"><span data-stu-id="208c5-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="208c5-119">Per creare un oggetto WSHttpBinding che usa le credenziali di Windows e la protezione dei messaggio</span><span class="sxs-lookup"><span data-stu-id="208c5-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="208c5-120">Il codice di questa procedura viene inserito all'inizio del metodo `Run` della classe `Test` nel codice del servizio riportato nella sezione Esempio.</span><span class="sxs-lookup"><span data-stu-id="208c5-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="208c5-121">Creare un'istanza della classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="208c5-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="208c5-122">Impostare la proprietà <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> della classe <xref:System.ServiceModel.WSHttpSecurity> su <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="208c5-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="208c5-123">Impostare la proprietà <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> della classe <xref:System.ServiceModel.MessageSecurityOverHttp> su <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="208c5-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="208c5-124">Il codice per questa procedura è il seguente:</span><span class="sxs-lookup"><span data-stu-id="208c5-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="208c5-125">Uso dell'associazione in un servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-125">Using the Binding in a Service</span></span>

<span data-ttu-id="208c5-126">Si tratta della seconda procedura, in cui viene illustrato l'uso dell'associazione in un servizio self-hosted.</span><span class="sxs-lookup"><span data-stu-id="208c5-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="208c5-127">Per ulteriori informazioni sui servizi di hosting, vedere [servizi di hosting](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="208c5-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="208c5-128">Per usare un'associazione in un servizio</span><span class="sxs-lookup"><span data-stu-id="208c5-128">To use a binding in a service</span></span>

1. <span data-ttu-id="208c5-129">Inserire il codice di questa procedura dopo il codice della procedura precedente.</span><span class="sxs-lookup"><span data-stu-id="208c5-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="208c5-130">Creare una variabile <xref:System.Type> denominata `contractType` e assegnarle il tipo dell'interfaccia (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="208c5-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="208c5-131">Quando si usa Visual Basic, usare `GetType` l'operatore. Quando C#si usa, `typeof` usare la parola chiave.</span><span class="sxs-lookup"><span data-stu-id="208c5-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="208c5-132">Creare una seconda variabile <xref:System.Type> denominata `serviceType` e assegnarle il tipo del contratto implementato (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="208c5-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="208c5-133">Creare un'istanza della classe <xref:System.Uri> denominata `baseAddress` con l'indirizzo di base del servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="208c5-134">L'indirizzo di base deve avere uno schema corrispondente al trasporto.</span><span class="sxs-lookup"><span data-stu-id="208c5-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="208c5-135">In questo caso, lo schema di trasporto è HTTP e l'indirizzo include il Uniform Resource Identifier speciale (URI) "localhost" e un numero di porta (8036), nonché un indirizzo endpoint di base ("serviceModelSamples/) `http://localhost:8036/serviceModelSamples/`:.</span><span class="sxs-lookup"><span data-stu-id="208c5-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="208c5-136">Creare un'istanza della classe <xref:System.ServiceModel.ServiceHost> class con le variabili `serviceType` e `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="208c5-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="208c5-137">Aggiungere un endpoint al servizio tramite l'interfaccia `contractType`, l'associazione e un nome di endpoint (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="208c5-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="208c5-138">Un client deve concatenare l'indirizzo di base e il nome dell'endpoint quando avvia una chiamata al servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="208c5-139">Chiamare il metodo <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> per avviare il servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="208c5-140">Il codice per questa procedura viene illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="208c5-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="208c5-141">Uso dell'associazione in un client</span><span class="sxs-lookup"><span data-stu-id="208c5-141">Using the Binding in a Client</span></span>

<span data-ttu-id="208c5-142">In questa procedura viene illustrato come generare un proxy che comunica con il servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="208c5-143">Il proxy viene generato con lo [strumento ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) che usa i metadati del servizio per creare il proxy.</span><span class="sxs-lookup"><span data-stu-id="208c5-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="208c5-144">In questa procedura viene anche creata un'istanza della classe <xref:System.ServiceModel.WSHttpBinding> per comunicare con il servizio, quindi viene chiamato il servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="208c5-145">In questo esempio, per creare il client viene usato solo codice.</span><span class="sxs-lookup"><span data-stu-id="208c5-145">This example uses only code to create the client.</span></span> <span data-ttu-id="208c5-146">In alternativa, è possibile usare un file di configurazione, illustrato nella sezione successiva a questa procedura.</span><span class="sxs-lookup"><span data-stu-id="208c5-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="208c5-147">Per usare un'associazione in un client con codice</span><span class="sxs-lookup"><span data-stu-id="208c5-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="208c5-148">Usare lo strumento SvcUtil.exe per generare il codice del proxy tramite i metadati del servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="208c5-149">Per altre informazioni, vedere [Procedura: Creazione di un](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)client.</span><span class="sxs-lookup"><span data-stu-id="208c5-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="208c5-150">Il codice proxy generato eredita dalla <xref:System.ServiceModel.ClientBase%601> classe, che garantisce che ogni client disponga dei costruttori, dei metodi e delle proprietà necessari per comunicare con un servizio WCF.</span><span class="sxs-lookup"><span data-stu-id="208c5-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="208c5-151">In questo esempio, il codice generato include la classe `CalculatorClient` che implementa l'interfaccia `ICalculator`, consentendo la compatibilità con il codice del servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="208c5-152">Il codice di questa procedura viene inserito all'inizio del metodo `Main` del programma client.</span><span class="sxs-lookup"><span data-stu-id="208c5-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="208c5-153">Creare un'istanza della classe <xref:System.ServiceModel.WSHttpBinding> e impostarne la modalità di sicurezza su `Message` e il tipo di credenziale client su `Windows`.</span><span class="sxs-lookup"><span data-stu-id="208c5-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="208c5-154">Nell'esempio viene denominata la variabile `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="208c5-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="208c5-155">Creare un'istanza della classe <xref:System.ServiceModel.EndpointAddress> denominata `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="208c5-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="208c5-156">Inizializzare l'istanza con l'indirizzo di base concatenato al nome dell'endpoint.</span><span class="sxs-lookup"><span data-stu-id="208c5-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="208c5-157">Creare un'istanza della classe client generata con le variabili `serviceAddress` e `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="208c5-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="208c5-158">Chiamare il metodo <xref:System.ServiceModel.ClientBase%601.Open%2A>, come mostrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="208c5-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="208c5-159">Chiamare il servizio e visualizzare i risultati.</span><span class="sxs-lookup"><span data-stu-id="208c5-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="208c5-160">Uso del file di configurazione</span><span class="sxs-lookup"><span data-stu-id="208c5-160">Using the Configuration File</span></span>

<span data-ttu-id="208c5-161">Anziché creare l'associazione con codice procedurale, è possibile usare il codice seguente illustrato per la sezione dell'associazione del file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="208c5-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="208c5-162">Se non è già stato definito un servizio, vedere [progettazione e implementazione di servizi](../../../docs/framework/wcf/designing-and-implementing-services.md)e [configurazione dei servizi](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="208c5-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="208c5-163">Questo codice di configurazione viene usato nei file di configurazione del servizio e del client.</span><span class="sxs-lookup"><span data-stu-id="208c5-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="208c5-164">Per abilitare la protezione del trasferimento in un servizio in un dominio Windows usando la configurazione</span><span class="sxs-lookup"><span data-stu-id="208c5-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="208c5-165">Aggiungere un [ \<elemento WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) alla [ \<sezione bindings >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento del file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="208c5-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="208c5-166">Aggiungere un elemento`binding`< > all'elemento <`WSHttpBinding`> e impostare l' `configurationName` attributo su un valore appropriato per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="208c5-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="208c5-167">Aggiungere un elemento`security`< > e impostare l' `mode` attributo su Message.</span><span class="sxs-lookup"><span data-stu-id="208c5-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="208c5-168">Aggiungere un elemento`message`< > e impostare l' `clientCredentialType` attributo su Windows.</span><span class="sxs-lookup"><span data-stu-id="208c5-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="208c5-169">Nel file di configurazione del servizio, sostituire la sezione `<bindings>` con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="208c5-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="208c5-170">Se non si dispone già di un file di configurazione del servizio, vedere [utilizzo delle associazioni per configurare servizi e client](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="208c5-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="208c5-171">Uso dell'associazione in un client</span><span class="sxs-lookup"><span data-stu-id="208c5-171">Using the Binding in a Client</span></span>

<span data-ttu-id="208c5-172">In questa procedura viene illustrato come generare due file, un proxy che comunica con il servizio e un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="208c5-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="208c5-173">Vengono inoltre descritte le modifiche apportate al programma client, ovvero il terzo file usato nel client.</span><span class="sxs-lookup"><span data-stu-id="208c5-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="208c5-174">Per usare un'associazione in un client con configurazione</span><span class="sxs-lookup"><span data-stu-id="208c5-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="208c5-175">Usare lo strumento SvcUtil.exe per generare il codice proxy e il file di configurazione tramite i metadati del servizio.</span><span class="sxs-lookup"><span data-stu-id="208c5-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="208c5-176">Per altre informazioni, vedere [Procedura: Creazione di un](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)client.</span><span class="sxs-lookup"><span data-stu-id="208c5-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="208c5-177">Sostituire le [ \<associazioni >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sezione del file di configurazione generato con il codice di configurazione della sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="208c5-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="208c5-178">Il codice procedurale viene inserito all'inizio del metodo `Main` del programma client.</span><span class="sxs-lookup"><span data-stu-id="208c5-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="208c5-179">Creare un'istanza della classe client generata che passi il nome dell'associazione nel file di configurazione come parametro di input.</span><span class="sxs-lookup"><span data-stu-id="208c5-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="208c5-180">Chiamare il metodo <xref:System.ServiceModel.ClientBase%601.Open%2A>, come mostrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="208c5-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="208c5-181">Chiamare il servizio e visualizzare i risultati.</span><span class="sxs-lookup"><span data-stu-id="208c5-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="208c5-182">Esempio</span><span class="sxs-lookup"><span data-stu-id="208c5-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="208c5-183">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="208c5-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="208c5-184">Strumento ServiceModel Metadata Utility Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="208c5-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="208c5-185">Procedura: Creazione di un client</span><span class="sxs-lookup"><span data-stu-id="208c5-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="208c5-186">Protezione dei servizi</span><span class="sxs-lookup"><span data-stu-id="208c5-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="208c5-187">Panoramica della sicurezza</span><span class="sxs-lookup"><span data-stu-id="208c5-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
