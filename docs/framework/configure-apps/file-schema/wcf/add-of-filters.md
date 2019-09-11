---
title: <add> di <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850557"
---
# <a name="add-of-filters"></a><span data-ttu-id="6bf97-102">\<aggiungere > di \<filtri ></span><span class="sxs-lookup"><span data-stu-id="6bf97-102">\<add> of \<filters></span></span>
<span data-ttu-id="6bf97-103">Filtro XPath che specifica il tipo di messaggio da registrare.</span><span class="sxs-lookup"><span data-stu-id="6bf97-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="6bf97-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6bf97-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6bf97-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6bf97-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6bf97-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> di diagnostica**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="6bf97-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="6bf97-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> messageLogging**](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="6bf97-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="6bf97-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtra >** ](filters.md)</span><span class="sxs-lookup"><span data-stu-id="6bf97-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="6bf97-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="6bf97-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bf97-110">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6bf97-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bf97-111">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6bf97-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6bf97-112">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="6bf97-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bf97-113">Attributi</span><span class="sxs-lookup"><span data-stu-id="6bf97-113">Attributes</span></span>  
  
|<span data-ttu-id="6bf97-114">Attributo</span><span class="sxs-lookup"><span data-stu-id="6bf97-114">Attribute</span></span>|<span data-ttu-id="6bf97-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6bf97-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6bf97-116">filtro</span><span class="sxs-lookup"><span data-stu-id="6bf97-116">filter</span></span>|<span data-ttu-id="6bf97-117">Stringa che specifica una query su un documento XML definito da un'espressione di XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="6bf97-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="6bf97-118">Per altre informazioni, vedere <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="6bf97-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6bf97-119">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6bf97-119">Child Elements</span></span>  
 <span data-ttu-id="6bf97-120">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="6bf97-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6bf97-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6bf97-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6bf97-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="6bf97-122">Element</span></span>|<span data-ttu-id="6bf97-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6bf97-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bf97-124">\<filters></span><span class="sxs-lookup"><span data-stu-id="6bf97-124">\<filters></span></span>](filters.md)|<span data-ttu-id="6bf97-125">Contiene una raccolta di filtri di XPath usati per controllare il tipo di messaggio registrato.</span><span class="sxs-lookup"><span data-stu-id="6bf97-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bf97-126">Note</span><span class="sxs-lookup"><span data-stu-id="6bf97-126">Remarks</span></span>  
 <span data-ttu-id="6bf97-127">I filtri vengono applicati solo al livello di trasporto, specificato da `logMessagesAtTransportLevel` impostato `true`.</span><span class="sxs-lookup"><span data-stu-id="6bf97-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="6bf97-128">I filtri non influiscono sulla registrazione dei messaggi a livello di servizio e in formato non valido.</span><span class="sxs-lookup"><span data-stu-id="6bf97-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="6bf97-129">Per aggiungere un filtro alla raccolta, usare la parola chiave `add`.</span><span class="sxs-lookup"><span data-stu-id="6bf97-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="6bf97-130">Quando sono definiti uno o più filtri, solo i messaggi che corrispondono almeno a uno dei filtri vengono registrati.</span><span class="sxs-lookup"><span data-stu-id="6bf97-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="6bf97-131">Se non è definito alcun filtro, passeranno tutti i messaggi.</span><span class="sxs-lookup"><span data-stu-id="6bf97-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="6bf97-132">I filtri supportano la sintassi Xpath completa e sono applicati nell'ordine in cui vengono visualizzati nel file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="6bf97-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="6bf97-133">Un filtro sintatticamente errato determina un'eccezione di configurazione.</span><span class="sxs-lookup"><span data-stu-id="6bf97-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="6bf97-134">Nell'esempio seguente viene illustrato come configurare un filtro che registra solo messaggi con una sezione intestazione SOAP.</span><span class="sxs-lookup"><span data-stu-id="6bf97-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bf97-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="6bf97-135">Example</span></span>  
 <span data-ttu-id="6bf97-136">Nell'esempio seguente viene illustrato come configurare un filtro che registra solo messaggi con una sezione intestazione SOAP.</span><span class="sxs-lookup"><span data-stu-id="6bf97-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="6bf97-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6bf97-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="6bf97-138">Configurazione della registrazione dei messaggi</span><span class="sxs-lookup"><span data-stu-id="6bf97-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="6bf97-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="6bf97-139">\<messageLogging></span></span>](messagelogging.md)
