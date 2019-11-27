---
title: Implementazione del pattern di controllo RangeValue di automazione interfaccia utente
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435112"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="1621a-102">Implementazione del pattern di controllo RangeValue di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="1621a-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="1621a-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="1621a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1621a-104">Per informazioni aggiornate su [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere [Windows Automation API: automazione interfaccia utente](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="1621a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="1621a-105">In questo argomento vengono presentate le linee guida e le convenzioni per l'implementazione di <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluse le informazioni relative a eventi e proprietà.</span><span class="sxs-lookup"><span data-stu-id="1621a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="1621a-106">Alla fine della panoramica sono elencati collegamenti ad altro materiale di riferimento.</span><span class="sxs-lookup"><span data-stu-id="1621a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="1621a-107">Il pattern di controllo <xref:System.Windows.Automation.RangeValuePattern> viene usato per supportare i controlli che possono impostare un valore in un intervallo.</span><span class="sxs-lookup"><span data-stu-id="1621a-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="1621a-108">Per esempi di controlli che implementano questo pattern di controllo, vedere [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1621a-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="1621a-109">Linee guida e convenzioni di implementazione</span><span class="sxs-lookup"><span data-stu-id="1621a-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="1621a-110">Quando si implementa il pattern di controllo RangeValue, tenere presenti le linee guida e le convenzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1621a-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="1621a-111">I controlli consentono la ricalibrazione delle relative proprietà supportate in base alle preferenze utente o alle impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="1621a-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="1621a-112">Un esempio di questo è un controllo termometro che può essere impostato per visualizzare la temperatura in gradi Fahrenheit o Celsius.</span><span class="sxs-lookup"><span data-stu-id="1621a-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="1621a-113">I controlli che dispongono di valori di intervallo ambigui, ad esempio le barre di avanzamento o i dispositivi di scorrimento, devono avere questi valori normalizzati.</span><span class="sxs-lookup"><span data-stu-id="1621a-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="1621a-114">![Indicatore di stato.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="1621a-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="1621a-115">Esempio di un indicatore di stato in cui valore è di tipo Integer e i relativi valori di proprietà minimo e massimo sono normalizzati rispettivamente a 0 e 100</span><span class="sxs-lookup"><span data-stu-id="1621a-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="1621a-116">Membri obbligatori per IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="1621a-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="1621a-117">Membro obbligatorio</span><span class="sxs-lookup"><span data-stu-id="1621a-117">Required member</span></span>|<span data-ttu-id="1621a-118">Tipo di membro</span><span class="sxs-lookup"><span data-stu-id="1621a-118">Member type</span></span>|<span data-ttu-id="1621a-119">Note</span><span class="sxs-lookup"><span data-stu-id="1621a-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="1621a-120">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1621a-120">Property</span></span>|<span data-ttu-id="1621a-121">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="1621a-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1621a-122">Property</span></span>|<span data-ttu-id="1621a-123">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="1621a-124">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1621a-124">Property</span></span>|<span data-ttu-id="1621a-125">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="1621a-126">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1621a-126">Property</span></span>|<span data-ttu-id="1621a-127">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="1621a-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1621a-128">Property</span></span>|<span data-ttu-id="1621a-129">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="1621a-130">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1621a-130">Property</span></span>|<span data-ttu-id="1621a-131">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="1621a-132">Metodi</span><span class="sxs-lookup"><span data-stu-id="1621a-132">Methods</span></span>|<span data-ttu-id="1621a-133">Nessuna</span><span class="sxs-lookup"><span data-stu-id="1621a-133">None</span></span>|  
  
 <span data-ttu-id="1621a-134">Questo pattern di controllo non è associato a eventi.</span><span class="sxs-lookup"><span data-stu-id="1621a-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="1621a-135">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="1621a-135">Exceptions</span></span>  
 <span data-ttu-id="1621a-136">I provider devono generare le eccezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="1621a-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="1621a-137">Tipo di eccezione</span><span class="sxs-lookup"><span data-stu-id="1621a-137">Exception type</span></span>|<span data-ttu-id="1621a-138">Condizione</span><span class="sxs-lookup"><span data-stu-id="1621a-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="1621a-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> viene chiamato con un valore che è maggiore di <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> o minore di <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="1621a-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1621a-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1621a-140">See also</span></span>

- [<span data-ttu-id="1621a-141">Panoramica dei pattern di controllo per l'automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="1621a-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="1621a-142">Supportare pattern di controllo in un provider di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="1621a-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="1621a-143">UI Automation Control Patterns for Clients</span><span class="sxs-lookup"><span data-stu-id="1621a-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="1621a-144">Panoramica dell'albero di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="1621a-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="1621a-145">Usare la memorizzazione nella cache in automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="1621a-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
