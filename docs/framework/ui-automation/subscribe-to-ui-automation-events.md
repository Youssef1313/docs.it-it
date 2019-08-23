---
title: Sottoscrivere gli eventi di automazione interfaccia utente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: fa3e289f042af3e55e8fc56528c29d5701c33d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961137"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="64990-102">Sottoscrivere gli eventi di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="64990-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="64990-103">Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="64990-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="64990-104">Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="64990-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="64990-105">Questo argomento illustra come sottoscrivere gli eventi generati dai provider di automazione interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="64990-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64990-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="64990-106">Example</span></span>  
 <span data-ttu-id="64990-107">Il codice di esempio seguente registra un gestore eventi per l'evento che viene generato quando viene richiamato un controllo, ad esempio un pulsante, e lo rimuove quando il form dell'applicazione viene chiuso.</span><span class="sxs-lookup"><span data-stu-id="64990-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="64990-108">L'evento viene identificato da un oggetto <xref:System.Windows.Automation.AutomationEvent> passato come parametro a <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="64990-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="64990-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="64990-109">Example</span></span>  
 <span data-ttu-id="64990-110">L'esempio seguente illustra come usare [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] per sottoscrivere un evento generato quando lo stato attivo cambia.</span><span class="sxs-lookup"><span data-stu-id="64990-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="64990-111">Il gestore eventi non è registrato in un metodo che può essere chiamato all'arresto dell'applicazione o quando la notifica degli eventi dell'interfaccia utente non è più necessaria.</span><span class="sxs-lookup"><span data-stu-id="64990-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="64990-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="64990-112">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="64990-113">Panoramica degli eventi di automazione interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="64990-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
