---
ms.openlocfilehash: 88e00454894c8404fd48e92404e35ae27fa056f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235425"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>TreeViewItem WPF va usato in una TreeView

|   |   |
|---|---|
|Dettagli|È stata introdotta una modifica nella versione 4.5 che limita l'uso di elementi <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> all'esterno di una <xref:System.Windows.Controls.TreeView?displayProperty=name>. Il problema può presentarsi nelle condizioni seguenti:<ul><li>L'elemento padre visivo di <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> non è un pannello. (L'elemento padre di un <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> generato per una <xref:System.Windows.Controls.TreeView?displayProperty=name> sarà un pannello)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> è un discendente di un <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> che funge da &quot;host di elementi&quot; per un controllo elenco (ListBox, DataGrid, ListView e così via). La virtualizzazione non deve essere abilitata.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> prevede lo scorrimento per elementi (<code>ScrollUnit=&quot;Item&quot;</code>).</li><li>Qualcuno chiama <code>VirtualizingStackPanel.MakeVisible(v)</code> per scorrere fino a un elemento <code>v</code> e visualizzarlo. Questa operazione può essere eseguita in modo esplicito o implicito in diversi modi. Probabilmente il modo più comune è il semplice clic su <code>v</code> per spostare lo stato attivo della tastiera sull'elemento.</li><li>La catena elemento padre visivo da <code>v</code> a <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> passa attraverso <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>.</li></ul>In altre parole, questo si verifica quando si usa un elemento <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> all'esterno di un <xref:System.Windows.Controls.TreeView?displayProperty=name> e l'utente fa clic su un discendente di <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> per visualizzarlo. Se non vi sono discendenti attivabili per <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> non si noterà mai il problema. Un esempio di situazione in cui si verifica questo problema è quando un <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> corrisponde alla radice di un DataTemplate. Quando si verifica il problema, viene generata un'eccezione InvalidCastException all'interno del framework WPF.|
|Suggerimento|Verrà reso disponibile un hotfix per questo problema.|
|Ambito|Secondario|
|Versione|4.5|
|Tipo|Runtime|
