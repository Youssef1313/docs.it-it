---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399080"
---
# <a name="workflowruntime"></a><span data-ttu-id="a697c-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="a697c-101">\<workflowRuntime></span></span>
<span data-ttu-id="a697c-102">Specifica le impostazioni per un'istanza <xref:System.Workflow.Runtime.WorkflowRuntime> di per l'hosting di servizi di Windows Communication Foundation (WCF) basati sul flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="a697c-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
<span data-ttu-id="a697c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a697c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a697c-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a697c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a697c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamenti >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a697c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a697c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a697c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="a697c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamento >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a697c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="a697c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowRuntime**</span><span class="sxs-lookup"><span data-stu-id="a697c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a697c-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a697c-109">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a697c-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="a697c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a697c-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="a697c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a697c-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="a697c-112">Attributes</span></span>  
  
|<span data-ttu-id="a697c-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="a697c-113">Attribute</span></span>|<span data-ttu-id="a697c-114">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="a697c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a697c-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="a697c-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="a697c-116">Valore <xref:System.TimeSpan> facoltativo che specifica la durata massima di memorizzazione in stato inattivo di un'istanza del flusso di lavoro prima che venga interrotta o scaricata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a697c-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="a697c-117">Se l'attributo `PersistenceService` di workflowruntime esegue il metodo unloadOnIdle, questo attributo viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="a697c-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="a697c-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="a697c-118">enablePerformanceCounters</span></span>|<span data-ttu-id="a697c-119">Valore booleano facoltativo che specifica se i contatori delle prestazioni sono attivi.</span><span class="sxs-lookup"><span data-stu-id="a697c-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="a697c-120">I contatori delle prestazioni forniscono informazioni su varie statistiche correlate al flusso di lavoro, ma provocano una riduzione delle prestazioni quando il motore di runtime del flusso di lavoro viene avviato e quando le istanze del flusso di lavoro sono in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="a697c-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="a697c-121">Il valore predefinito è `true`.</span><span class="sxs-lookup"><span data-stu-id="a697c-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="a697c-122">name</span><span class="sxs-lookup"><span data-stu-id="a697c-122">name</span></span>|<span data-ttu-id="a697c-123">Stringa contenente il nome del motore di runtime del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="a697c-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="a697c-124">Il nome viene usato in output per distinguere questo runtime da altri runtime che potrebbero essere in esecuzione nel sistema, ad esempio nei contatori delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="a697c-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="a697c-125">Il valore predefinito è una stringa vuota.</span><span class="sxs-lookup"><span data-stu-id="a697c-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="a697c-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="a697c-126">validateOnCreate</span></span>|<span data-ttu-id="a697c-127">Valore booleano facoltativo che specifica se all'apertura dell'elemento WorkflowServiceHost verrà eseguita la convalida della definizione del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="a697c-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="a697c-128">Quando questo attributo viene impostato su `true`, la convalida del flusso di lavoro viene eseguita ogni volta che viene chiamato il metodo `WorkflowServiceHost.Open`.</span><span class="sxs-lookup"><span data-stu-id="a697c-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="a697c-129">Se vengono individuati errori di convalida, viene generata un'eccezione <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException>.</span><span class="sxs-lookup"><span data-stu-id="a697c-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="a697c-130">Quando questa proprietà è impostata su `false` la definizione del flusso di lavoro non viene convalidata.</span><span class="sxs-lookup"><span data-stu-id="a697c-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="a697c-131">Il valore predefinito di questa proprietà è `true`.</span><span class="sxs-lookup"><span data-stu-id="a697c-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a697c-132">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="a697c-132">Child Elements</span></span>  
  
|<span data-ttu-id="a697c-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="a697c-133">Element</span></span>|<span data-ttu-id="a697c-134">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a697c-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a697c-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="a697c-135">commonParameters</span></span>|<span data-ttu-id="a697c-136">Raccolta di parametri comuni usati dai servizi.</span><span class="sxs-lookup"><span data-stu-id="a697c-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="a697c-137">Questa raccolta in genere contiene la stringa di connessione del database che potrebbe essere condivisa dai servizi durevoli.</span><span class="sxs-lookup"><span data-stu-id="a697c-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="a697c-138">services</span><span class="sxs-lookup"><span data-stu-id="a697c-138">services</span></span>|<span data-ttu-id="a697c-139">Raccolta di servizi da aggiungere al motore di <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="a697c-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="a697c-140">Gli elementi sono di tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a697c-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="a697c-141">I servizi specificati nella raccolta verranno inizializzati dal motore di runtime del flusso di lavoro e verranno aggiunti ai relativi servizi quando verrà chiamato il costruttore <xref:System.Workflow.Runtime.WorkflowRuntime> appropriato.</span><span class="sxs-lookup"><span data-stu-id="a697c-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="a697c-142">Pertanto, i servizi specificati nella raccolta devono seguire regole precise riguardanti le firme dei relativi costruttori.</span><span class="sxs-lookup"><span data-stu-id="a697c-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="a697c-143">Per altre informazioni, vedere <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a697c-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a697c-144">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="a697c-144">Parent Elements</span></span>  
  
|<span data-ttu-id="a697c-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="a697c-145">Element</span></span>|<span data-ttu-id="a697c-146">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a697c-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a697c-147">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a697c-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a697c-148">Specifica un elemento di comportamento.</span><span class="sxs-lookup"><span data-stu-id="a697c-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a697c-149">Note</span><span class="sxs-lookup"><span data-stu-id="a697c-149">Remarks</span></span>  
 <span data-ttu-id="a697c-150">Per ulteriori informazioni sull'utilizzo di un file di configurazione per controllare il comportamento <xref:System.Workflow.Runtime.WorkflowRuntime> di un oggetto di un'applicazione host Windows Workflow Foundation, vedere [file di configurazione del flusso di lavoro](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a697c-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a697c-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="a697c-151">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="a697c-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a697c-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="a697c-153">[File di configurazione del flusso di lavoro](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a697c-153">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
