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
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementazione del pattern di controllo GridItem di automazione interfaccia utente
> [!NOTE]
> Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.  
  
 In questo argomento vengono presentate le linee guida e le convenzioni per l'implementazione di <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluse le informazioni relative alle proprietà. Alla fine della panoramica sono elencati collegamenti a ulteriore materiale di riferimento.  
  
 Il pattern di controllo <xref:System.Windows.Automation.GridItemPattern> viene usato per supportare singoli controlli figlio di contenitori che implementano <xref:System.Windows.Automation.Provider.IGridProvider>. Per esempi di controlli che implementano questo pattern di controllo, vedere [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Linee guida e convenzioni di implementazione  
 Quando si implementa <xref:System.Windows.Automation.Provider.IGridProvider>, tenere presenti le linee guida e le convenzioni seguenti:  
  
- Le coordinate della griglia sono in base zero. Le coordinate della cella in alto a sinistra sono infatti (0, 0).  
  
- Le celle unite segnaleranno le proprietà <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> in base alla cella di aggancio sottostante, secondo quanto definito dal provider di automazione interfaccia utente. In genere si tratterà della riga o della colonna più in alto e più a sinistra.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider> non consente di apportare modifiche attive alla griglia, ad esempio l'unione o la separazione di celle.  
  
- I controlli che implementano <xref:System.Windows.Automation.Provider.IGridItemProvider> in genere possono essere attraversati (ovvero, il client di automazione interfaccia utente può passare ai controlli adiacenti) usando la tastiera.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Membri obbligatori per IGridItemProvider  
 Le proprietà e i metodi seguenti sono obbligatori per l'implementazione di <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Membri obbligatori|Tipo di membro|Note|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Proprietà|Nessuna|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Proprietà|Nessuna|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Proprietà|Nessuna|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Proprietà|Nessuna|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Proprietà|Nessuna|  
  
 Questo pattern di controllo non è associato a metodi o eventi.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Eccezioni  
 Questo pattern di controllo non è associato a eccezioni.  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica dei pattern di controllo per l'automazione interfaccia utente](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Supportare pattern di controllo in un provider di automazione interfaccia utente](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Pattern di controllo di automazione interfaccia utente per i client](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementazione del pattern di controllo Grid di automazione interfaccia utente](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [Panoramica dell'albero di automazione interfaccia utente](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usare la memorizzazione nella cache in automazione interfaccia utente](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
