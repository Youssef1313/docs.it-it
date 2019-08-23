---
title: <participants>di WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 44962c12f0c7260799d04f26b3fa16016edd2b7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932822"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="5bfcc-102">\<partecipanti > di WCF</span><span class="sxs-lookup"><span data-stu-id="5bfcc-102">\<participants> of WCF</span></span>
<span data-ttu-id="5bfcc-103">Configurare un elenco di partecipanti del rilevamento che ascoltano i record di rilevamento generati direttamente durante la fase di esecuzione e li elaborano in base alle impostazioni configurate.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="5bfcc-104">Tali impostazioni includono la scrittura in un output specifico, ad esempio file, console, ETW, l'elaborazione/aggregazione dei record o qualsiasi altra combinazione che potrebbe essere richiesta.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="5bfcc-105">Per altre informazioni sui partecipanti di rilevamento e rilevamento del flusso di lavoro, vedere Rilevamento e traccia [del flusso di lavoro](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) [partecipanti](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="5bfcc-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="5bfcc-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5bfcc-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5bfcc-107">\<rilevamento ></span><span class="sxs-lookup"><span data-stu-id="5bfcc-107">\<tracking></span></span>  
<span data-ttu-id="5bfcc-108">\<partecipanti ></span><span class="sxs-lookup"><span data-stu-id="5bfcc-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfcc-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5bfcc-109">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bfcc-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5bfcc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5bfcc-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bfcc-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="5bfcc-112">Attributes</span></span>  
 <span data-ttu-id="5bfcc-113">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5bfcc-114">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5bfcc-114">Child Elements</span></span>  
  
|<span data-ttu-id="5bfcc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="5bfcc-115">Element</span></span>|<span data-ttu-id="5bfcc-116">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="5bfcc-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bfcc-117">\<add></span><span class="sxs-lookup"><span data-stu-id="5bfcc-117">\<add></span></span>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="5bfcc-118">Contiene impostazioni per un partecipante del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bfcc-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5bfcc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5bfcc-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="5bfcc-120">Element</span></span>|<span data-ttu-id="5bfcc-121">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5bfcc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bfcc-122">\<rilevamento ></span><span class="sxs-lookup"><span data-stu-id="5bfcc-122">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="5bfcc-123">Rappresenta una sezione di configurazione per la definizione delle impostazioni di rilevamento di un servizio flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bfcc-124">Note</span><span class="sxs-lookup"><span data-stu-id="5bfcc-124">Remarks</span></span>  
 <span data-ttu-id="5bfcc-125">I partecipanti del rilevamento vengono usati per ottenere i dati di rilevamento generati dal flusso di lavoro e archiviarli in supporti differenti.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="5bfcc-126">Analogamente, è anche possibile eseguire qualsiasi operazione di post-elaborazione sui record di rilevamento all'interno del partecipante del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="5bfcc-127">Più partecipanti del rilevamento possono usare simultaneamente gli eventi di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="5bfcc-128">Ogni partecipante del rilevamento può essere associato a un profilo di rilevamento diverso.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="5bfcc-129">Viene fornito un partecipante del rilevamento standard che scrive i record di rilevamento in una sessione ETW.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="5bfcc-130">Il partecipante viene configurato su un servizio flusso di lavoro aggiungendo un comportamento specifico del rilevamento in un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="5bfcc-131">L'abilitazione di un partecipante del rilevamento ETW consente la visualizzazione dei record di rilevamento nel Visualizzatore eventi.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="5bfcc-132">Se tale partecipante non soddisfa i propri requisiti, è anche possibile scrivere un partecipante del rilevamento personalizzato.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bfcc-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="5bfcc-133">Example</span></span>  
 <span data-ttu-id="5bfcc-134">Nell'esempio di configurazione seguente viene mostrato il partecipante del rilevamento ETW standard configurato nel file Web.config.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="5bfcc-135">L'ID del provider usato dal partecipante del rilevamento ETW per scrivere i record di rilevamento in ETW è definito nella sezione `<diagnostics>`.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="5bfcc-136">Al partecipante di rilevamento è associato un profilo per specificare i record di rilevamento che ha sottoscritto.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="5bfcc-137">Tale profilo è definito dall'attributo `profileName` dell'elemento `<add>`.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="5bfcc-138">Dopo aver definito tali elementi, il partecipante del rilevamento viene aggiunto al comportamento del servizio `<etwTracking>`,</span><span class="sxs-lookup"><span data-stu-id="5bfcc-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="5bfcc-139">che aggiungerà i partecipanti del rilevamento selezionati alle estensioni dell'istanza del flusso di lavoro, in modo che inizino a ricevere i record di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="5bfcc-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="5bfcc-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5bfcc-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="5bfcc-141">Rilevamento e analisi del flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="5bfcc-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5bfcc-142">Partecipanti di rilevamento</span><span class="sxs-lookup"><span data-stu-id="5bfcc-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
