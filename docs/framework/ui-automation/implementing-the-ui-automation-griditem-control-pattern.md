---
title: Implementazione del pattern di controllo GridItem di automazione interfaccia utente
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 1fa0de86ee59a48d0d64156b41ad2db794dff761
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968891"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="9a055-102">Implementazione del pattern di controllo GridItem di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="9a055-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9a055-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="9a055-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9a055-104">Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="9a055-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9a055-105">In questo argomento vengono presentate le linee guida e le convenzioni per l'implementazione di <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluse le informazioni relative alle proprietà.</span><span class="sxs-lookup"><span data-stu-id="9a055-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="9a055-106">Alla fine della panoramica sono elencati collegamenti a ulteriore materiale di riferimento.</span><span class="sxs-lookup"><span data-stu-id="9a055-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9a055-107">Il pattern di controllo <xref:System.Windows.Automation.GridItemPattern> viene usato per supportare singoli controlli figlio di contenitori che implementano <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="9a055-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="9a055-108">Per esempi di controlli che implementano questo pattern di controllo, vedere [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9a055-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9a055-109">Linee guida e convenzioni di implementazione</span><span class="sxs-lookup"><span data-stu-id="9a055-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9a055-110">Quando si implementa <xref:System.Windows.Automation.Provider.IGridProvider>, tenere presenti le linee guida e le convenzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a055-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="9a055-111">Le coordinate della griglia sono in base zero. Le coordinate della cella in alto a sinistra sono infatti (0, 0).</span><span class="sxs-lookup"><span data-stu-id="9a055-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="9a055-112">Le celle unite segnaleranno le proprietà <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> in base alla cella di aggancio sottostante, secondo quanto definito dal provider di automazione interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="9a055-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="9a055-113">In genere si tratterà della riga o della colonna più in alto e più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="9a055-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="9a055-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> non consente di apportare modifiche attive alla griglia, ad esempio l'unione o la separazione di celle.</span><span class="sxs-lookup"><span data-stu-id="9a055-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="9a055-115">I controlli che implementano <xref:System.Windows.Automation.Provider.IGridItemProvider> in genere possono essere attraversati (ovvero, il client di automazione interfaccia utente può passare ai controlli adiacenti) usando la tastiera.</span><span class="sxs-lookup"><span data-stu-id="9a055-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="9a055-116">Membri obbligatori per IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="9a055-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="9a055-117">Le proprietà e i metodi seguenti sono obbligatori per l'implementazione di <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="9a055-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="9a055-118">Membri obbligatori</span><span class="sxs-lookup"><span data-stu-id="9a055-118">Required members</span></span>|<span data-ttu-id="9a055-119">Tipo di membro</span><span class="sxs-lookup"><span data-stu-id="9a055-119">Member type</span></span>|<span data-ttu-id="9a055-120">Note</span><span class="sxs-lookup"><span data-stu-id="9a055-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="9a055-121">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a055-121">Property</span></span>|<span data-ttu-id="9a055-122">Nessuna</span><span class="sxs-lookup"><span data-stu-id="9a055-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="9a055-123">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a055-123">Property</span></span>|<span data-ttu-id="9a055-124">Nessuna</span><span class="sxs-lookup"><span data-stu-id="9a055-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="9a055-125">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a055-125">Property</span></span>|<span data-ttu-id="9a055-126">Nessuna</span><span class="sxs-lookup"><span data-stu-id="9a055-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="9a055-127">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a055-127">Property</span></span>|<span data-ttu-id="9a055-128">Nessuna</span><span class="sxs-lookup"><span data-stu-id="9a055-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="9a055-129">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9a055-129">Property</span></span>|<span data-ttu-id="9a055-130">Nessuna</span><span class="sxs-lookup"><span data-stu-id="9a055-130">None</span></span>|  
  
 <span data-ttu-id="9a055-131">Questo pattern di controllo non è associato a metodi o eventi.</span><span class="sxs-lookup"><span data-stu-id="9a055-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9a055-132">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="9a055-132">Exceptions</span></span>  
 <span data-ttu-id="9a055-133">Questo pattern di controllo non è associato a eccezioni.</span><span class="sxs-lookup"><span data-stu-id="9a055-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a055-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a055-134">See also</span></span>

- [<span data-ttu-id="9a055-135">Panoramica dei pattern di controllo per l'automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="9a055-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9a055-136">Supportare pattern di controllo in un provider di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="9a055-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9a055-137">Pattern di controllo di automazione interfaccia utente per i client</span><span class="sxs-lookup"><span data-stu-id="9a055-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9a055-138">Implementazione del pattern di controllo Grid di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="9a055-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="9a055-139">Panoramica dell'albero di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="9a055-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="9a055-140">Usare la memorizzazione nella cache in automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="9a055-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
