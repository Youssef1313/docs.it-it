---
title: 'Procedura: scambiare messaggi in una sessione affidabile'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141686"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="8b5e0-102">Procedura: scambiare messaggi in una sessione affidabile</span><span class="sxs-lookup"><span data-stu-id="8b5e0-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="8b5e0-103">In questo argomento vengono delineati i passaggi necessari per attivare una sessione affidabile utilizzando una delle associazioni fornite dal sistema che supportano tale sessione, ma non per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="8b5e0-104">Una sessione affidabile viene abilitata in modo imperativo tramite codice o in modo dichiarativo nel file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="8b5e0-105">Questa procedura usa i file di configurazione del client e del servizio per abilitare la sessione affidabile e per stabilire che i messaggi arrivano nello stesso ordine in cui sono stati inviati.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="8b5e0-106">La parte principale di questa procedura è che l'elemento di configurazione dell'endpoint contiene un `bindingConfiguration` attributo che fa riferimento a una configurazione dell'associazione denominata `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="8b5e0-107">L'elemento di configurazione dell' [**associazione\<** ](../../configure-apps/file-schema/wcf/bindings.md) fa riferimento a questo nome per abilitare sessioni affidabili impostando l'attributo `enabled` dell'elemento [ **\<> ReliableSession**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) su `true`.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="8b5e0-108">Le garanzie di recapito ordinato per la sessione affidabile vengono specificate impostando l'attributo `ordered` su `true`.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="8b5e0-109">Per la copia di origine di questo esempio, vedere [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="8b5e0-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="8b5e0-110">Configurare il servizio con WSHttpBinding per l'utilizzo di una sessione affidabile</span><span class="sxs-lookup"><span data-stu-id="8b5e0-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="8b5e0-111">Definire un contratto di servizio per il tipo di servizio.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="8b5e0-112">Implementare il contratto di servizio in una classe del servizio.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="8b5e0-113">Si noti che le informazioni sull'indirizzo o sull'associazione non sono specificate nell'implementazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="8b5e0-114">Non è necessario scrivere codice per recuperare l'indirizzo o le informazioni di binding dal file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="8b5e0-115">Creare un file *Web. config* per configurare un endpoint per la `CalculatorService` che utilizza la <xref:System.ServiceModel.WSHttpBinding> con una sessione affidabile abilitata e il recapito ordinato dei messaggi necessari.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="8b5e0-116">Creare un file *Service. svc* contenente la riga:</span><span class="sxs-lookup"><span data-stu-id="8b5e0-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="8b5e0-117">Inserire il file *Service. svc* nella directory virtuale Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="8b5e0-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="8b5e0-118">Configurare il client con WSHttpBinding per l'utilizzo di una sessione affidabile</span><span class="sxs-lookup"><span data-stu-id="8b5e0-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="8b5e0-119">Utilizzare lo [strumento ServiceModel Metadata Utility Tool (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dalla riga di comando per generare codice dai metadati del servizio:</span><span class="sxs-lookup"><span data-stu-id="8b5e0-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="8b5e0-120">Il client generato contiene l'interfaccia `ICalculator` che definisce il contratto di servizio che l'implementazione client deve soddisfare.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="8b5e0-121">L'applicazione client generata contiene inoltre l'implementazione di `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="8b5e0-122">Si noti che le informazioni sull'indirizzo e sull'associazione non sono specificate in un punto qualsiasi all'interno dell'implementazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="8b5e0-123">Non è necessario scrivere codice per recuperare l'indirizzo o le informazioni di binding dal file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="8b5e0-124">*Svcutil. exe* genera inoltre la configurazione per il client che utilizza la classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="8b5e0-125">Denominare il file di configurazione *app. config* quando si usa Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="8b5e0-126">Creare un'istanza della `ClientCalculator` in un'applicazione e chiamare le operazioni del servizio.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="8b5e0-127">Compilare ed eseguire il client.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="8b5e0-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="8b5e0-128">Example</span></span>

<span data-ttu-id="8b5e0-129">Diverse associazioni fornite dal sistema supportano sessioni affidabili per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="8b5e0-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="8b5e0-130">tra cui:</span><span class="sxs-lookup"><span data-stu-id="8b5e0-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="8b5e0-131">Per un esempio di come creare un'associazione personalizzata che supporta sessioni affidabili, vedere [procedura: creare un'associazione di sessione affidabile personalizzata con https](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="8b5e0-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b5e0-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8b5e0-132">See also</span></span>

- [<span data-ttu-id="8b5e0-133">Sessioni affidabili</span><span class="sxs-lookup"><span data-stu-id="8b5e0-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
