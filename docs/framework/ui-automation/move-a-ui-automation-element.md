---
title: Spostare un elemento di automazione interfaccia utente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 43b1e005cdb499fae920a0999feaa56c5409f653
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964687"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="e7e12-102">Spostare un elemento di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="e7e12-102">Move a UI Automation Element</span></span>
> [!NOTE]
> <span data-ttu-id="e7e12-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e7e12-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e7e12-104">Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="e7e12-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e7e12-105">In questo esempio viene illustrato come spostare un elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] in una posizione dello schermo specificata.</span><span class="sxs-lookup"><span data-stu-id="e7e12-105">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7e12-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="e7e12-106">Example</span></span>  
 <span data-ttu-id="e7e12-107">Nell'esempio seguente vengono usati i pattern di controllo <xref:System.Windows.Automation.WindowPattern> e <xref:System.Windows.Automation.TransformPattern> per spostare a livello di codice un'applicazione di destinazione [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] target application to discrete screen locations e track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span><span class="sxs-lookup"><span data-stu-id="e7e12-107">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="e7e12-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7e12-108">See also</span></span>

- [<span data-ttu-id="e7e12-109">Esempio WindowPattern</span><span class="sxs-lookup"><span data-stu-id="e7e12-109">WindowPattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
