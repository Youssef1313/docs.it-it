---
title: Implementazione del pattern di controllo RangeValue di automazione interfaccia utente
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 70ee5009e2763348f7c69613a1776e02e82e0391
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932129"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="0dcc3-102">Implementazione del pattern di controllo RangeValue di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="0dcc3-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="0dcc3-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0dcc3-104">Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0dcc3-105">In questo argomento vengono presentate le linee guida e le convenzioni per l'implementazione di <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluse le informazioni relative a eventi e proprietà.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="0dcc3-106">Alla fine della panoramica sono elencati collegamenti ad altro materiale di riferimento.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="0dcc3-107">Il pattern di controllo <xref:System.Windows.Automation.RangeValuePattern> viene usato per supportare i controlli che possono impostare un valore in un intervallo.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="0dcc3-108">Per esempi di controlli che implementano questo pattern di controllo, vedere [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0dcc3-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="0dcc3-109">Linee guida e convenzioni di implementazione</span><span class="sxs-lookup"><span data-stu-id="0dcc3-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="0dcc3-110">Quando si implementa il pattern di controllo RangeValue, tenere presenti le linee guida e le convenzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="0dcc3-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="0dcc3-111">I controlli consentono la ricalibrazione delle relative proprietà supportate in base alle preferenze utente o alle impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="0dcc3-112">Un esempio di questo è un controllo termometro che può essere impostato per visualizzare la temperatura in gradi Fahrenheit o Celsius.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="0dcc3-113">I controlli che dispongono di valori di intervallo ambigui, ad esempio le barre di avanzamento o i dispositivi di scorrimento, devono avere questi valori normalizzati.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="0dcc3-114">![Indicatore di stato.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="0dcc3-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="0dcc3-115">Esempio di un indicatore di stato in cui valore è di tipo Integer e i relativi valori di proprietà minimo e massimo sono normalizzati rispettivamente a 0 e 100</span><span class="sxs-lookup"><span data-stu-id="0dcc3-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="0dcc3-116">Membri obbligatori per IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="0dcc3-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="0dcc3-117">Membro obbligatorio</span><span class="sxs-lookup"><span data-stu-id="0dcc3-117">Required member</span></span>|<span data-ttu-id="0dcc3-118">Tipo di membro</span><span class="sxs-lookup"><span data-stu-id="0dcc3-118">Member type</span></span>|<span data-ttu-id="0dcc3-119">Note</span><span class="sxs-lookup"><span data-stu-id="0dcc3-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="0dcc3-120">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0dcc3-120">Property</span></span>|<span data-ttu-id="0dcc3-121">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="0dcc3-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0dcc3-122">Property</span></span>|<span data-ttu-id="0dcc3-123">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="0dcc3-124">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0dcc3-124">Property</span></span>|<span data-ttu-id="0dcc3-125">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="0dcc3-126">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0dcc3-126">Property</span></span>|<span data-ttu-id="0dcc3-127">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="0dcc3-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0dcc3-128">Property</span></span>|<span data-ttu-id="0dcc3-129">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="0dcc3-130">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0dcc3-130">Property</span></span>|<span data-ttu-id="0dcc3-131">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="0dcc3-132">Metodi</span><span class="sxs-lookup"><span data-stu-id="0dcc3-132">Methods</span></span>|<span data-ttu-id="0dcc3-133">Nessuna</span><span class="sxs-lookup"><span data-stu-id="0dcc3-133">None</span></span>|  
  
 <span data-ttu-id="0dcc3-134">Questo pattern di controllo non è associato a eventi.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="0dcc3-135">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="0dcc3-135">Exceptions</span></span>  
 <span data-ttu-id="0dcc3-136">I provider devono generare le eccezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="0dcc3-137">Tipo di eccezione</span><span class="sxs-lookup"><span data-stu-id="0dcc3-137">Exception type</span></span>|<span data-ttu-id="0dcc3-138">Condizione</span><span class="sxs-lookup"><span data-stu-id="0dcc3-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="0dcc3-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> viene chiamato con un valore che è maggiore di <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> o minore di <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="0dcc3-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dcc3-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0dcc3-140">See also</span></span>

- [<span data-ttu-id="0dcc3-141">Panoramica dei pattern di controllo per l'automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="0dcc3-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0dcc3-142">Supportare pattern di controllo in un provider di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="0dcc3-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="0dcc3-143">Pattern di controllo di automazione interfaccia utente per i client</span><span class="sxs-lookup"><span data-stu-id="0dcc3-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0dcc3-144">Panoramica dell'albero di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="0dcc3-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="0dcc3-145">Usare la memorizzazione nella cache in automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="0dcc3-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
