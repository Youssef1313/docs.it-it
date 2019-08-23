---
title: <add> di <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926663"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="43bcb-102">\<aggiungere > di \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="43bcb-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="43bcb-103">Rappresenta un mapping del protocollo predefinito tra uno schema del protocollo di trasporto (ad esempio http, NET. TCP, NET. pipe e così via) e un'associazione Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="43bcb-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="43bcb-104">Quando si creano endpoint predefiniti in fase di esecuzione, WCF esamina i mapping configurati e decide il binding da usare per un determinato indirizzo di base.</span><span class="sxs-lookup"><span data-stu-id="43bcb-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="43bcb-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="43bcb-105">\<system.serviceModel></span></span>  
<span data-ttu-id="43bcb-106">\<> protocolMapping</span><span class="sxs-lookup"><span data-stu-id="43bcb-106">\<protocolMapping></span></span>  
<span data-ttu-id="43bcb-107">\<add></span><span class="sxs-lookup"><span data-stu-id="43bcb-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43bcb-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43bcb-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43bcb-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="43bcb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43bcb-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="43bcb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43bcb-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="43bcb-111">Attributes</span></span>  
  
|<span data-ttu-id="43bcb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="43bcb-112">Element</span></span>|<span data-ttu-id="43bcb-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="43bcb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43bcb-114">binding</span><span class="sxs-lookup"><span data-stu-id="43bcb-114">binding</span></span>|<span data-ttu-id="43bcb-115">Stringa che specifica il tipo di associazione da usare per un endpoint durante la creazione dell'endpoint predefinito.</span><span class="sxs-lookup"><span data-stu-id="43bcb-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="43bcb-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="43bcb-116">bindingConfiguration</span></span>|<span data-ttu-id="43bcb-117">Stringa che specifica il nome della sezione di configurazione dell'associazione alla quale fare riferimento.</span><span class="sxs-lookup"><span data-stu-id="43bcb-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="43bcb-118">scheme</span><span class="sxs-lookup"><span data-stu-id="43bcb-118">scheme</span></span>|<span data-ttu-id="43bcb-119">Schema del protocollo di trasporto da usare per l'endpoint predefinito.</span><span class="sxs-lookup"><span data-stu-id="43bcb-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43bcb-120">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="43bcb-120">Child Elements</span></span>  
 <span data-ttu-id="43bcb-121">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="43bcb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43bcb-122">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="43bcb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="43bcb-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="43bcb-123">Element</span></span>|<span data-ttu-id="43bcb-124">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="43bcb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43bcb-125">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="43bcb-125">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="43bcb-126">Rappresenta una sezione di configurazione per la definizione di mapping dei protocolli predefiniti tra gli schemi del protocollo di trasporto (ad esempio http, NET. TCP, NET. pipe e così via) e le associazioni Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="43bcb-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43bcb-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="43bcb-127">Example</span></span>  
 <span data-ttu-id="43bcb-128">Nell'esempio di configurazione seguente viene illustrato il mapping del protocollo predefinito nel file machine.config.</span><span class="sxs-lookup"><span data-stu-id="43bcb-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="43bcb-129">È possibile eseguire l'override di questo mapping predefinito al livello di computer modificando il file machine.config.</span><span class="sxs-lookup"><span data-stu-id="43bcb-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="43bcb-130">In alternativa, se si desidera eseguirne l'override solo nell'ambito di un'applicazione, è possibile eseguire l'override di questa sezione all'interno del file di configurazione dell'applicazione e modificare il mapping per i singoli schemi di protocollo.</span><span class="sxs-lookup"><span data-stu-id="43bcb-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="43bcb-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43bcb-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
