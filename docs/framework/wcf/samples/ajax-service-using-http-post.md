---
title: Servizio AJAX con il protocollo HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972015"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="53254-102">Servizio AJAX con il protocollo HTTP POST</span><span class="sxs-lookup"><span data-stu-id="53254-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="53254-103">In questo esempio viene illustrato come utilizzare Windows Communication Foundation (WCF) per creare un servizio AJAX (ASP.NET Asynchronous JavaScript and XML) che utilizza HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="53254-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="53254-104">È possibile accedere a questo servizio utilizzando il codice JavaScript di base da un client del browser Web.</span><span class="sxs-lookup"><span data-stu-id="53254-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="53254-105">Questo esempio si basa sull'esempio di [servizio AJAX di base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) . l'unica differenza tra i due esempi è l'uso di HTTP POST anziché HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="53254-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="53254-106">Il supporto AJAX in Windows Communication Foundation (WCF) è ottimizzato per l'uso con ASP.NET `ScriptManager` AJAX tramite il controllo.</span><span class="sxs-lookup"><span data-stu-id="53254-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="53254-107">Per un esempio di utilizzo di WCF con ASP.NET AJAX, vedere gli [esempi di AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="53254-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="53254-108">La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="53254-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="53254-109">Il servizio nell'esempio seguente è un servizio WCF senza codice specifico per AJAX.</span><span class="sxs-lookup"><span data-stu-id="53254-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="53254-110">Se l' <xref:System.ServiceModel.Web.WebInvokeAttribute> attributo viene applicato a un'operazione o l' <xref:System.ServiceModel.Web.WebGetAttribute> attributo non viene applicato, viene utilizzato il verbo HTTP predefinito ("post").</span><span class="sxs-lookup"><span data-stu-id="53254-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="53254-111">Le richieste POST sono più difficili da costruire rispetto alle richieste GET, ma non vengono memorizzate nella cache; utilizzare le richieste POST per tutte le operazioni in cui la memorizzazione nella cache non è appropriata.</span><span class="sxs-lookup"><span data-stu-id="53254-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="53254-112">Creare un endpoint AJAX sul servizio utilizzando <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, proprio come nell'esempio del servizio AJAX di base.</span><span class="sxs-lookup"><span data-stu-id="53254-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="53254-113">A differenza delle richieste GET, non è possibile richiamare servizi POST dal browser.</span><span class="sxs-lookup"><span data-stu-id="53254-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="53254-114">Ad esempio, la navigazione a `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` genera un errore, perché il servizio post prevede che i `n1` parametri e `n2` vengano inviati nel corpo del messaggio in formato JSON e non nell'URL.</span><span class="sxs-lookup"><span data-stu-id="53254-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="53254-115">La pagina Web PostAjaxClientPage.aspx del client contiene il codice ASP.NET per richiamare il servizio ogni qualvolta che l'utente fa clic su uno dei pulsanti di operazione nella pagina.</span><span class="sxs-lookup"><span data-stu-id="53254-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="53254-116">Il servizio risponde in modo analogo all'esempio di [servizio AJAX di base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , con la richiesta GET.</span><span class="sxs-lookup"><span data-stu-id="53254-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53254-117">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="53254-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="53254-118">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="53254-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="53254-119">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="53254-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53254-120">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="53254-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="53254-121">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="53254-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="53254-122">Assicurarsi di eseguire le istruzioni di installazione [una sola volta la procedura di installazione per gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53254-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="53254-123">Compilare la soluzione PostAjaxService. sln come descritto in [compilazione degli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53254-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="53254-124">Passare a `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (non aprire PostAjaxClientPage. aspx nel browser dalla directory del progetto).</span><span class="sxs-lookup"><span data-stu-id="53254-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
