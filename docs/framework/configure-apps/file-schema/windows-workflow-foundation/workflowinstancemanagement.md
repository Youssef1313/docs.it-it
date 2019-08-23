---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947154"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="8f6a3-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="8f6a3-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="8f6a3-102">Comportamento del servizio che consente di specificare impostazioni che controllano la modalità di esecuzione delle istanze del flusso di lavoro, inclusa la persistenza, il comportamento delle eccezioni non gestite e il comportamento di inattività.</span><span class="sxs-lookup"><span data-stu-id="8f6a3-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="8f6a3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8f6a3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8f6a3-104">\<comportamenti ></span><span class="sxs-lookup"><span data-stu-id="8f6a3-104">\<behaviors></span></span>  
<span data-ttu-id="8f6a3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8f6a3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8f6a3-106">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8f6a3-106">\<behavior></span></span>  
<span data-ttu-id="8f6a3-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="8f6a3-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f6a3-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8f6a3-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f6a3-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8f6a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8f6a3-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="8f6a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f6a3-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="8f6a3-111">Attributes</span></span>  
  
|<span data-ttu-id="8f6a3-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="8f6a3-112">Attribute</span></span>|<span data-ttu-id="8f6a3-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="8f6a3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f6a3-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="8f6a3-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="8f6a3-115">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8f6a3-115">Child Elements</span></span>  
 <span data-ttu-id="8f6a3-116">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="8f6a3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f6a3-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8f6a3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8f6a3-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f6a3-118">Element</span></span>|<span data-ttu-id="8f6a3-119">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="8f6a3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f6a3-120">\<comportamento > di \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8f6a3-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8f6a3-121">Specifica un elemento di comportamento.</span><span class="sxs-lookup"><span data-stu-id="8f6a3-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f6a3-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8f6a3-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
