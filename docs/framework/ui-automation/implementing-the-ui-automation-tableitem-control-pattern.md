---
title: Implementazione del pattern di controllo TableItem di automazione interfaccia utente
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 8f368fee6df6ebe5455f2029670e90f036d3d89a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932097"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementazione del pattern di controllo TableItem di automazione interfaccia utente
> [!NOTE]
> Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.  
  
 In questo argomento vengono presentate le linee guida e le convenzioni per l'implementazione di <xref:System.Windows.Automation.Provider.ITableItemProvider>, incluse le informazioni relative a eventi e proprietà. Alla fine della panoramica sono elencati collegamenti a ulteriore materiale di riferimento.  
  
 Il pattern di controllo <xref:System.Windows.Automation.TableItemPattern> viene usato per supportare i controlli figlio di contenitori che implementano <xref:System.Windows.Automation.Provider.ITableProvider>. L'accesso alla funzionalità delle singole celle viene fornito dall'implementazione simultanea obbligatoria di <xref:System.Windows.Automation.Provider.IGridItemProvider>. Questo pattern di controllo è analogo a <xref:System.Windows.Automation.Provider.IGridItemProvider> con la differenza che i controlli che implementano <xref:System.Windows.Automation.Provider.ITableItemProvider> devono esporre a livello di codice la relazione tra la singola cella e le informazioni di righe e colonne. Per esempi di controlli che implementano questo pattern di controllo, vedere [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Linee guida e convenzioni di implementazione  
  
- Per la funzionalità degli elementi della griglia correlata, vedere [implementazione del pattern di controllo GridItem di automazione interfaccia utente](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>Membri obbligatori per ITableItemProvider  
  
|Membro obbligatorio|Tipo di membro|Note|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Metodo|Nessuna|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Metodo|Nessuna|  
  
 Questo pattern di controllo non è associato a proprietà o eventi.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Eccezioni  
 Questo pattern di controllo non è associato a eccezioni.  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica dei pattern di controllo per l'automazione interfaccia utente](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Supportare pattern di controllo in un provider di automazione interfaccia utente](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Pattern di controllo di automazione interfaccia utente per i client](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementazione del pattern di controllo Table di automazione interfaccia utente](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [Implementazione del pattern di controllo GridItem di automazione interfaccia utente](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [Panoramica dell'albero di automazione interfaccia utente](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usare la memorizzazione nella cache in automazione interfaccia utente](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
