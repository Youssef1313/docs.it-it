---
title: 'Procedura: Esporre un feed come Atom e RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: f31f24cfc18f2c56539fe2b4623d54fe77a27797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950602"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="f0f1b-102">Procedura: Esporre un feed come Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="f0f1b-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="f0f1b-103">Windows Communication Foundation (WCF) consente di creare un servizio che espone un feed di diffusione.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="f0f1b-104">In questo argomento viene illustrato come creare un servizio di diffusione che espone un feed di diffusione usando sia Atom 1.0 sia RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="f0f1b-105">Questo servizio espone un endpoint che può restituire uno dei due formati di diffusione.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="f0f1b-106">Per motivi di semplicità, il servizio usato in questo esempio è indipendente.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="f0f1b-107">In un ambiente di produzione un servizio di questo tipo verrebbe ospitato da IIS o WAS.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="f0f1b-108">Per ulteriori informazioni sulle diverse opzioni di hosting WCF, vedere [hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="f0f1b-108">For more information about the different WCF hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="f0f1b-109">Per creare un servizio di diffusione di base</span><span class="sxs-lookup"><span data-stu-id="f0f1b-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="f0f1b-110">Definire un contratto di servizio usando un'interfaccia contrassegnata con l'attributo <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="f0f1b-111">Ogni operazione esposta come feed di diffusione restituisce un oggetto <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="f0f1b-112">Si notino i parametri per <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="f0f1b-113">`UriTemplate` specifica l'URL usato per richiamare questa operazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="f0f1b-114">La stringa per questo parametro contiene valori letterali e una variabile racchiusa tra parentesi graffe ({*Format*}).</span><span class="sxs-lookup"><span data-stu-id="f0f1b-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="f0f1b-115">Questa variabile corrisponde al parametro `format` dell'operazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="f0f1b-116">Per altre informazioni, vedere <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="f0f1b-117">`BodyStyle` incide sul modo in cui vengono scritti i messaggi inviati e ricevuti da e verso questa operazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="f0f1b-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifica che i dati inviati da e verso questa operazione del servizio non vengono incapsulati in elementi XML definiti dall'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="f0f1b-119">Per altre informazioni, vedere <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="f0f1b-120">Usare <xref:System.ServiceModel.ServiceKnownTypeAttribute> per specificare i tipi restituiti dalle operazioni del servizio in questa interfaccia.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="f0f1b-121">Implementare il contratto di servizio</span><span class="sxs-lookup"><span data-stu-id="f0f1b-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="f0f1b-122">Creare un oggetto <xref:System.ServiceModel.Syndication.SyndicationFeed> e aggiungere un autore, una categoria e una descrizione.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="f0f1b-123">Creare diversi oggetti <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="f0f1b-124">Aggiungere gli oggetti <xref:System.ServiceModel.Syndication.SyndicationItem> al feed.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="f0f1b-125">Usare il parametro di formato per restituire il formato richiesto.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="f0f1b-126">Per ospitare il servizio</span><span class="sxs-lookup"><span data-stu-id="f0f1b-126">To host the service</span></span>  
  
1. <span data-ttu-id="f0f1b-127">Creare un oggetto <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="f0f1b-128">La classe <xref:System.ServiceModel.Web.WebServiceHost> aggiunge automaticamente un endpoint nell'indirizzo di base del servizio, a meno che non ne sia specificato uno nel codice o nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="f0f1b-129">Poiché in questo esempio non è specificato alcun endpoint, viene esposto l'endpoint predefinito.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="f0f1b-130">Aprire l'host del servizio, caricare il feed dal servizio, visualizzare il feed e aspettare che l'utente prema INVIO.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="f0f1b-131">Per chiamare GetBlog con HTTP GET</span><span class="sxs-lookup"><span data-stu-id="f0f1b-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="f0f1b-132">Aprire Internet Explorer, digitare l'URL seguente e premere INVIO: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="f0f1b-133">L'URL contiene l'indirizzo di base del servizio (`http://localhost:8000/BlogService`), l'indirizzo relativo dell'endpoint e l'operazione del servizio da chiamare.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="f0f1b-134">Per chiamare GetBlog() dal codice</span><span class="sxs-lookup"><span data-stu-id="f0f1b-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="f0f1b-135">Creare un <xref:System.Xml.XmlReader> con l'indirizzo di base e il metodo che si sta chiamando.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="f0f1b-136">Chiamare il metodo statico <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> passando l'oggetto <xref:System.Xml.XmlReader> appena creato.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="f0f1b-137">Verrà in tal modo richiamata l'operazione del servizio e verrà popolato un nuovo <xref:System.ServiceModel.Syndication.SyndicationFeed> con il formattatore restituito dall'operazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="f0f1b-138">Accedere all'oggetto feed.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="f0f1b-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="f0f1b-139">Example</span></span>  
 <span data-ttu-id="f0f1b-140">Di seguito è riportato il codice completo per questo esempio.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0f1b-141">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="f0f1b-141">Compiling the Code</span></span>  
 <span data-ttu-id="f0f1b-142">Durante la compilazione del codice precedente, fare riferimento a System.ServiceModel.dll e a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="f0f1b-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f1b-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f0f1b-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
