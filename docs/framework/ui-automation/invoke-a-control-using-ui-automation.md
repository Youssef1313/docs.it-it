---
title: Richiamare un controllo utilizzando automazione interfaccia utente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923730"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="85dd4-102">Richiamare un controllo utilizzando automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="85dd4-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="85dd4-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="85dd4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="85dd4-104">Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="85dd4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="85dd4-105">In questo argomento viene illustrato come eseguire le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="85dd4-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="85dd4-106">Trovare un controllo che corrisponda a condizioni di proprietà specifiche scorrendo la visualizzazione controlli dell'albero di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] per l'applicazione di destinazione.</span><span class="sxs-lookup"><span data-stu-id="85dd4-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="85dd4-107">Creare un <xref:System.Windows.Automation.AutomationElement> per ogni controllo.</span><span class="sxs-lookup"><span data-stu-id="85dd4-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="85dd4-108">Ottenere un oggetto <xref:System.Windows.Automation.InvokePattern> da qualsiasi elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] trovato che supporta il pattern di controllo <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="85dd4-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="85dd4-109">Usare <xref:System.Windows.Automation.InvokePattern.Invoke%2A> per richiamare il controllo da un gestore eventi client.</span><span class="sxs-lookup"><span data-stu-id="85dd4-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85dd4-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="85dd4-110">Example</span></span>  
 <span data-ttu-id="85dd4-111">Questo esempio usa il metodo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> della classe <xref:System.Windows.Automation.AutomationElement> per generare un oggetto <xref:System.Windows.Automation.InvokePattern> e richiamare un controllo mediante il metodo <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="85dd4-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="85dd4-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="85dd4-112">See also</span></span>

- [<span data-ttu-id="85dd4-113">Esempio InvokePattern, ExpandCollapsePattern e TogglePattern</span><span class="sxs-lookup"><span data-stu-id="85dd4-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
