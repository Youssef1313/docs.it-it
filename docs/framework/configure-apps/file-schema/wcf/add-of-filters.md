---
title: <add> di <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926692"
---
# <a name="add-of-filters"></a><span data-ttu-id="e0bdb-102">\<aggiungere > di \<filtri ></span><span class="sxs-lookup"><span data-stu-id="e0bdb-102">\<add> of \<filters></span></span>
<span data-ttu-id="e0bdb-103">Filtro XPath che specifica il tipo di messaggio da registrare.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="e0bdb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e0bdb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0bdb-105">\<> di diagnostica</span><span class="sxs-lookup"><span data-stu-id="e0bdb-105">\<diagnostic></span></span>  
<span data-ttu-id="e0bdb-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="e0bdb-106">\<messageLogging></span></span>  
<span data-ttu-id="e0bdb-107">\<Filtra ></span><span class="sxs-lookup"><span data-stu-id="e0bdb-107">\<filters></span></span>  
<span data-ttu-id="e0bdb-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e0bdb-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bdb-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e0bdb-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0bdb-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e0bdb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e0bdb-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0bdb-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="e0bdb-112">Attributes</span></span>  
  
|<span data-ttu-id="e0bdb-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="e0bdb-113">Attribute</span></span>|<span data-ttu-id="e0bdb-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e0bdb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0bdb-115">filtro</span><span class="sxs-lookup"><span data-stu-id="e0bdb-115">filter</span></span>|<span data-ttu-id="e0bdb-116">Stringa che specifica una query su un documento XML definito da un'espressione di XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="e0bdb-117">Per altre informazioni, vedere <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0bdb-118">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e0bdb-118">Child Elements</span></span>  
 <span data-ttu-id="e0bdb-119">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0bdb-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e0bdb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e0bdb-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0bdb-121">Element</span></span>|<span data-ttu-id="e0bdb-122">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="e0bdb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0bdb-123">\<filters></span><span class="sxs-lookup"><span data-stu-id="e0bdb-123">\<filters></span></span>](filters.md)|<span data-ttu-id="e0bdb-124">Contiene una raccolta di filtri di XPath usati per controllare il tipo di messaggio registrato.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0bdb-125">Note</span><span class="sxs-lookup"><span data-stu-id="e0bdb-125">Remarks</span></span>  
 <span data-ttu-id="e0bdb-126">I filtri vengono applicati solo al livello di trasporto, specificato da `logMessagesAtTransportLevel` impostato `true`.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="e0bdb-127">I filtri non influiscono sulla registrazione dei messaggi a livello di servizio e in formato non valido.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="e0bdb-128">Per aggiungere un filtro alla raccolta, usare la parola chiave `add`.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="e0bdb-129">Quando sono definiti uno o più filtri, solo i messaggi che corrispondono almeno a uno dei filtri vengono registrati.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="e0bdb-130">Se non è definito alcun filtro, passeranno tutti i messaggi.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="e0bdb-131">I filtri supportano la sintassi Xpath completa e sono applicati nell'ordine in cui vengono visualizzati nel file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="e0bdb-132">Un filtro sintatticamente errato determina un'eccezione di configurazione.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="e0bdb-133">Nell'esempio seguente viene illustrato come configurare un filtro che registra solo messaggi con una sezione intestazione SOAP.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0bdb-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="e0bdb-134">Example</span></span>  
 <span data-ttu-id="e0bdb-135">Nell'esempio seguente viene illustrato come configurare un filtro che registra solo messaggi con una sezione intestazione SOAP.</span><span class="sxs-lookup"><span data-stu-id="e0bdb-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0bdb-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e0bdb-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="e0bdb-137">Configurazione della registrazione dei messaggi</span><span class="sxs-lookup"><span data-stu-id="e0bdb-137">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="e0bdb-138">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="e0bdb-138">\<messageLogging></span></span>](messagelogging.md)
