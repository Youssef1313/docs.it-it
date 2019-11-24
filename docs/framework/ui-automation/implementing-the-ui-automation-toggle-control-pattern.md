---
title: Implementazione del pattern di controllo Toggle di automazione interfaccia utente
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447068"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="a7c08-102">Implementazione del pattern di controllo Toggle di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="a7c08-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="a7c08-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a7c08-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a7c08-104">Per informazioni aggiornate su [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere l'argomento sull' [API Automazione interfaccia utente di Windows](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a7c08-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a7c08-105">In questo argomento vengono presentate le linee guida e le convenzioni per l'implementazione di <xref:System.Windows.Automation.Provider.IToggleProvider>, incluse le informazioni relative a metodi e proprietà.</span><span class="sxs-lookup"><span data-stu-id="a7c08-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="a7c08-106">Alla fine della panoramica sono elencati collegamenti ad altro materiale di riferimento.</span><span class="sxs-lookup"><span data-stu-id="a7c08-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a7c08-107">Il pattern di controllo <xref:System.Windows.Automation.TogglePattern> viene usato per supportare i controlli che possono scorrere un insieme di stati e gestire uno stato impostato.</span><span class="sxs-lookup"><span data-stu-id="a7c08-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="a7c08-108">Per esempi di controlli che implementano questo pattern di controllo, vedere [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a7c08-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a7c08-109">Linee guida e convenzioni di implementazione</span><span class="sxs-lookup"><span data-stu-id="a7c08-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a7c08-110">Quando si implementa il pattern di controllo Toggle, tenere presenti le linee guida e le convenzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a7c08-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="a7c08-111">I controlli che, una volta attivati, non mantengono lo stato, ad esempio pulsanti, pulsanti della barra degli strumenti e collegamenti ipertestuali, devono invece implementare <xref:System.Windows.Automation.Provider.IInvokeProvider> .</span><span class="sxs-lookup"><span data-stu-id="a7c08-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="a7c08-112">Un controllo deve scorrere i relativi <xref:System.Windows.Automation.ToggleState> nell'ordine seguente: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> e, se supportato, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="a7c08-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="a7c08-113"><xref:System.Windows.Automation.TogglePattern> non implementa un metodo SetState(newState) a causa di problemi relativi all'impostazione diretta di una casella di controllo a tre stati senza la possibilità di scorrere la relativa sequenza <xref:System.Windows.Automation.ToggleState> appropriata.</span><span class="sxs-lookup"><span data-stu-id="a7c08-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="a7c08-114">Il controllo RadioButton non implementa <xref:System.Windows.Automation.Provider.IToggleProvider>perché non è in grado di eseguire lo scorrimento tra gli stati validi.</span><span class="sxs-lookup"><span data-stu-id="a7c08-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="a7c08-115">Membri obbligatori per IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="a7c08-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="a7c08-116">Le proprietà e i metodi seguenti sono obbligatori per l'implementazione di <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="a7c08-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="a7c08-117">Membro obbligatorio</span><span class="sxs-lookup"><span data-stu-id="a7c08-117">Required member</span></span>|<span data-ttu-id="a7c08-118">Tipo di membro</span><span class="sxs-lookup"><span data-stu-id="a7c08-118">Member type</span></span>|<span data-ttu-id="a7c08-119">Note</span><span class="sxs-lookup"><span data-stu-id="a7c08-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="a7c08-120">Metodo</span><span class="sxs-lookup"><span data-stu-id="a7c08-120">Method</span></span>|<span data-ttu-id="a7c08-121">Nessuno</span><span class="sxs-lookup"><span data-stu-id="a7c08-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="a7c08-122">proprietà</span><span class="sxs-lookup"><span data-stu-id="a7c08-122">Property</span></span>|<span data-ttu-id="a7c08-123">Nessuno</span><span class="sxs-lookup"><span data-stu-id="a7c08-123">None</span></span>|  
  
 <span data-ttu-id="a7c08-124">Questo pattern di controllo non è associato a eventi.</span><span class="sxs-lookup"><span data-stu-id="a7c08-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="a7c08-125">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="a7c08-125">Exceptions</span></span>  
 <span data-ttu-id="a7c08-126">Questo pattern di controllo non è associato a eccezioni.</span><span class="sxs-lookup"><span data-stu-id="a7c08-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c08-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a7c08-127">See also</span></span>

- [<span data-ttu-id="a7c08-128">Panoramica dei pattern di controllo per l'automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="a7c08-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a7c08-129">Supportare pattern di controllo in un provider di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="a7c08-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="a7c08-130">Pattern di controllo di automazione interfaccia utente per i client</span><span class="sxs-lookup"><span data-stu-id="a7c08-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="a7c08-131">Ottenere lo stato di attivo/non attivo di una casella di controllo usando l'automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="a7c08-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="a7c08-132">Panoramica dell'albero di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="a7c08-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="a7c08-133">Usare la memorizzazione nella cache in automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="a7c08-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
