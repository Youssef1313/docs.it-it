---
title: Servizio AJAX con esempi JSON e XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 62c573a844ce5382308814342330f778fa041a69
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045199"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="8e851-102">Servizio AJAX con esempi JSON e XML</span><span class="sxs-lookup"><span data-stu-id="8e851-102">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="8e851-103">In questo esempio viene illustrato come utilizzare Windows Communication Foundation (WCF) per creare un servizio AJAX (Asynchronous JavaScript and XML) che restituisce i dati JavaScript Object Notation (JSON) o XML.</span><span class="sxs-lookup"><span data-stu-id="8e851-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="8e851-104">È possibile accedere a un servizio AJAX utilizzando codice JavaScript a partire da un client del browser Web.</span><span class="sxs-lookup"><span data-stu-id="8e851-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="8e851-105">Questo esempio si basa sull'esempio di [servizio AJAX di base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="8e851-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="8e851-106">A differenza degli altri esempi AJAX, questo esempio non utilizza ASP.NET AJAX e il controllo <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="8e851-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="8e851-107">Con alcune configurazioni aggiuntive, è possibile accedere ai servizi WCF AJAX da qualsiasi pagina HTML tramite JavaScript e questo scenario è illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="8e851-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="8e851-108">Per un esempio dell'uso di WCF con ASP.NET AJAX, vedere [esempi di AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="8e851-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="8e851-109">Questo esempio mostra come cambiare il tipo di risposta di un'operazione da JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="8e851-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="8e851-110">Questa funzionalità è disponibile indipendentemente dal fatto che il servizio sia configurato per l'accesso da ASP.NET AJAX o da una pagina client HTML/JavaScript semplice.</span><span class="sxs-lookup"><span data-stu-id="8e851-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="8e851-111">La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="8e851-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8e851-112">Per abilitare l'utilizzo di client AJAX non ASP.NET, utilizzare <xref:System.ServiceModel.Activation.WebServiceHostFactory> (non <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) nel file con estensione svc.</span><span class="sxs-lookup"><span data-stu-id="8e851-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="8e851-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> aggiunge un endpoint <xref:System.ServiceModel.Description.WebHttpEndpoint> standard al servizio.</span><span class="sxs-lookup"><span data-stu-id="8e851-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="8e851-114">L'endpoint è configurato in un indirizzo vuoto relativo al file con estensione svc; Ciò significa che l'indirizzo del servizio è `http://localhost/ServiceModelSamples/service.svc`, senza suffissi aggiuntivi oltre al nome dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="8e851-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>
```

<span data-ttu-id="8e851-115">La sezione seguente in Web.config può essere usata per effettuare modifiche di configurazione aggiuntive all'endpoint</span><span class="sxs-lookup"><span data-stu-id="8e851-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="8e851-116">Può essere rimossa se non sono necessarie modifiche aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="8e851-116">It can be removed if no extra changes are needed.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="8e851-117">Il formato di dati predefinito <xref:System.ServiceModel.Description.WebHttpEndpoint> per è XML, mentre il formato di dati <xref:System.ServiceModel.Description.WebScriptEndpoint> predefinito per è JSON.</span><span class="sxs-lookup"><span data-stu-id="8e851-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="8e851-118">Per ulteriori informazioni, vedere [creazione di servizi WCF AJAX senza ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="8e851-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="8e851-119">Il servizio nell'esempio seguente è un servizio WCF standard con due operazioni.</span><span class="sxs-lookup"><span data-stu-id="8e851-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="8e851-120">Entrambe le operazioni richiedono lo stile del corpo <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> sugli attributi <xref:System.ServiceModel.Web.WebGetAttribute> o <xref:System.ServiceModel.Web.WebInvokeAttribute> che è specifico del comportamento `webHttp` e non è rilevante per il cambiamento di formato JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="8e851-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="8e851-121">Il formato della risposta per l'operazione viene specificato come XML, ovvero l'impostazione predefinita per il comportamento del [ \<> WebHttp](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="8e851-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="8e851-122">Tuttavia, si consiglia di specificare esplicitamente il formato della risposta.</span><span class="sxs-lookup"><span data-stu-id="8e851-122">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="8e851-123">L'altra operazione utilizza l'attributo `WebInvokeAttribute` e specifica in modo esplicito JSON anziché XML per la risposta.</span><span class="sxs-lookup"><span data-stu-id="8e851-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="8e851-124">Si noti che in entrambi i casi le operazioni restituiscono un `MathResult`tipo complesso,, che è un tipo di contratto dati WCF standard.</span><span class="sxs-lookup"><span data-stu-id="8e851-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="8e851-125">La pagina Web client XmlAjaxClientPage. htm contiene codice JavaScript che richiama una delle due operazioni precedenti quando l'utente fa clic sui pulsanti **Esegui calcolo (Restituisci JSON)** o **Esegui calcolo (Restituisci XML)** nella pagina.</span><span class="sxs-lookup"><span data-stu-id="8e851-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="8e851-126">Il codice per richiamare il servizio costruisce un corpo JSON e lo invia utilizzando HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="8e851-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="8e851-127">La richiesta viene creata manualmente in JavaScript, a differenza dell'esempio di [servizio AJAX di base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) e degli altri esempi che usano ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="8e851-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

<span data-ttu-id="8e851-128">Quando il servizio risponde, la risposta viene visualizzata senza nessuna ulteriore elaborazione in una casella di testo nella pagina.</span><span class="sxs-lookup"><span data-stu-id="8e851-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="8e851-129">Viene implementata a mero scopo esemplificativo per consentire di osservare direttamente i formati dati XML e JSON utilizzati.</span><span class="sxs-lookup"><span data-stu-id="8e851-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="8e851-130">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="8e851-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8e851-131">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="8e851-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8e851-132">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="8e851-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e851-133">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="8e851-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8e851-134">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="8e851-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8e851-135">Assicurarsi di avere eseguito la [procedura di installazione singola per gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e851-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8e851-136">Compilare la soluzione XmlAjaxService. sln come descritto in [compilazione degli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e851-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="8e851-137">Passare a `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (non aprire XmlAjaxClientPage. htm nel browser dalla directory del progetto).</span><span class="sxs-lookup"><span data-stu-id="8e851-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e851-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8e851-138">See also</span></span>

- [<span data-ttu-id="8e851-139">Servizio AJAX con il protocollo HTTP POST</span><span class="sxs-lookup"><span data-stu-id="8e851-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
