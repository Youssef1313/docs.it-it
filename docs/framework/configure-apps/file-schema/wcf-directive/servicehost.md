---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: a56fb1bb9395425222347914fe3f4c17f1a451b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920331"
---
# <a name="servicehost"></a><span data-ttu-id="e8ee1-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="e8ee1-101">\@ServiceHost</span></span>
<span data-ttu-id="e8ee1-102">Associa la factory usata per creare l'host del servizio al servizio da ospitare e agli altri aspetti di programmazione necessari per accedere al codice host fornito nel file .svc o per compilarlo.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ee1-103">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8ee1-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="e8ee1-104">Attributi</span><span class="sxs-lookup"><span data-stu-id="e8ee1-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="e8ee1-105">Service</span><span class="sxs-lookup"><span data-stu-id="e8ee1-105">Service</span></span>  
 <span data-ttu-id="e8ee1-106">Nome del tipo CLR del servizio ospitato.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="e8ee1-107">Deve essere un nome completo di un tipo che implementa uno o più dei contatti del servizio.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="e8ee1-108">Factory</span><span class="sxs-lookup"><span data-stu-id="e8ee1-108">Factory</span></span>  
 <span data-ttu-id="e8ee1-109">Nome del tipo CLR della factory dell'host del servizio usato per creare un'istanza dell'host del servizio.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="e8ee1-110">L'attributo è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-110">This attribute is optional.</span></span> <span data-ttu-id="e8ee1-111">Se non viene specificato, viene usata la factory <xref:System.ServiceModel.Activation.ServiceHostFactory> predefinita, che restituisce un'istanza dell'host <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="e8ee1-112">Debug</span><span class="sxs-lookup"><span data-stu-id="e8ee1-112">Debug</span></span>  
 <span data-ttu-id="e8ee1-113">Indica se il servizio Windows Communication Foundation (WCF) deve essere compilato con simboli di debug.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="e8ee1-114">`true`Se il servizio WCF deve essere compilato con i simboli di debug; in caso `false`contrario,.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="e8ee1-115">Linguaggio</span><span class="sxs-lookup"><span data-stu-id="e8ee1-115">Language</span></span>  
 <span data-ttu-id="e8ee1-116">Specifica il linguaggio usato per la compilazione di tutto il codice inline contenuto nel file con estensione svc.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="e8ee1-117">I valori possono rappresentare qualsiasi linguaggio supportato da .NET, inclusi C#, VB e JS, che fanno riferimento, rispettivamente, a C#, Visual Basic .NET e JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="e8ee1-118">L'attributo è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="e8ee1-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="e8ee1-119">CodeBehind</span></span>  
 <span data-ttu-id="e8ee1-120">Specifica il file di origine per l'implementazione del servizio Web XML, quando la classe di implementazione non si trova nello stesso file e non è stata compilata in un assembly e inserita nella directory \Bin.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8ee1-121">Note</span><span class="sxs-lookup"><span data-stu-id="e8ee1-121">Remarks</span></span>  
 <span data-ttu-id="e8ee1-122">L' <xref:System.ServiceModel.ServiceHost> oggetto utilizzato per ospitare il servizio è un punto di estendibilità all'interno del modello di programmazione Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e8ee1-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="e8ee1-123">Poiché un modello di factory può essere un tipo polimorfico di cui l'ambiente host non deve creare un'istanza direttamente, tale modello viene usato per creare un'istanza dell'host <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="e8ee1-124">L'implementazione predefinita usa la factory <xref:System.ServiceModel.Activation.ServiceHostFactory> per creare un'istanza dell'host <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e8ee1-125">È tuttavia possibile specificare una factory personalizzata, ovvero una che restituisce l'host derivato, specificando il nome del tipo CLR dell'implementazione Factory nella [ \@direttiva ServiceHost](servicehost.md) .</span><span class="sxs-lookup"><span data-stu-id="e8ee1-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="e8ee1-126">Per usare la factory host del servizio personalizzata anziché la factory predefinita, è sufficiente specificare il nome del tipo nella [@ServiceHost](servicehost.md) direttiva, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="e8ee1-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="e8ee1-127">È consigliabile garantire che le implementazioni presentino la massima semplicità possibile.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="e8ee1-128">Se si usa un'elevata quantità di logica personalizzata, quest'ultima è più riutilizzabile se inserita nell'host anziché nella factory.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="e8ee1-129">Per abilitare un endpoint abilitato per AJAX per `MyService`, ad esempio, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> specificare `Factory` per il valore dell'attributo [@ServiceHost](servicehost.md) , anziché quello predefinito <xref:System.ServiceModel.Activation.ServiceHostFactory>, nella direttiva, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e8ee1-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8ee1-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="e8ee1-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8ee1-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8ee1-131">See also</span></span>

- [<span data-ttu-id="e8ee1-132">Host di servizi personalizzati</span><span class="sxs-lookup"><span data-stu-id="e8ee1-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
