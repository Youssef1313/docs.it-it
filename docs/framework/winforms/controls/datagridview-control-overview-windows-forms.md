---
title: Cenni preliminari sul controllo DataGridView (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 992bf57642c955a87cd7675e0bbe7c52131e8039
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969140"
---
# <a name="datagridview-control-overview-windows-forms"></a>Cenni preliminari sul controllo DataGridView (Windows Form)
> [!NOTE]
> Benché il controllo <xref:System.Windows.Forms.DataGridView> sostituisca il controllo <xref:System.Windows.Forms.DataGrid> aggiungendovi funzionalità, il controllo <xref:System.Windows.Forms.DataGrid> viene mantenuto per compatibilità con le versioni precedenti e per un eventuale uso futuro. Per altre informazioni, vedere [Differenze tra i controlli DataGridView e DataGrid Windows Form](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Con il <xref:System.Windows.Forms.DataGridView> controllo è possibile visualizzare e modificare i dati tabulari da molti tipi diversi di origini dati.  
  
 L'associazione di dati <xref:System.Windows.Forms.DataGridView> al controllo è semplice e intuitiva e, in molti casi, è semplice come impostare <xref:System.Windows.Forms.DataGridView.DataSource%2A> la proprietà. Quando si esegue l'associazione a un'origine dati che contiene più elenchi o tabelle, <xref:System.Windows.Forms.DataGridView.DataMember%2A> impostare la proprietà su una stringa che specifica l'elenco o la tabella a cui eseguire l'associazione.  
  
 Il <xref:System.Windows.Forms.DataGridView> controllo supporta il modello di data binding Windows Forms standard, in modo che venga associato alle istanze delle classi descritte nell'elenco seguente:  
  
- Qualsiasi classe che implementa l' <xref:System.Collections.IList> interfaccia, incluse le matrici unidimensionali.  
  
- Qualsiasi classe che implementa l' <xref:System.ComponentModel.IListSource> interfaccia, ad esempio le <xref:System.Data.DataTable> classi <xref:System.Data.DataSet> e.  
  
- Qualsiasi classe che implementa l' <xref:System.ComponentModel.IBindingList> interfaccia, ad esempio la <xref:System.ComponentModel.BindingList%601> classe.  
  
- Qualsiasi classe che implementa l' <xref:System.ComponentModel.IBindingListView> interfaccia, ad esempio la <xref:System.Windows.Forms.BindingSource> classe.  
  
 Il <xref:System.Windows.Forms.DataGridView> controllo supporta data binding alle proprietà pubbliche degli oggetti restituiti da queste interfacce o alla raccolta Properties restituita da un' <xref:System.ComponentModel.ICustomTypeDescriptor> interfaccia, se implementata sugli oggetti restituiti.  
  
 In genere, si eseguirà l' <xref:System.Windows.Forms.BindingSource> associazione a un componente <xref:System.Windows.Forms.BindingSource> e si associa il componente a un'altra origine dati o lo si popola con gli oggetti business. Il <xref:System.Windows.Forms.BindingSource> componente è l'origine dati preferita perché può essere associato a un'ampia gamma di origini dati e può risolvere molti problemi di data binding automaticamente. Per ulteriori informazioni, vedere [componente BindingSource](bindingsource-component.md).  
  
 Il <xref:System.Windows.Forms.DataGridView> controllo può essere usato anche in modalità non *associata* , senza archivio dati sottostante. Per un esempio di codice in cui viene usato <xref:System.Windows.Forms.DataGridView> un controllo non [associato, vedere Procedura dettagliata: Creazione di un controllo](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)DataGridView Windows Forms non associato.  
  
 Il <xref:System.Windows.Forms.DataGridView> controllo è altamente configurabile ed estendibile e fornisce molte proprietà, metodi ed eventi per personalizzarne l'aspetto e il comportamento. Quando si desidera che la Windows Forms Application visualizzi dati tabulari, è <xref:System.Windows.Forms.DataGridView> consigliabile utilizzare il controllo prima di altri <xref:System.Windows.Forms.DataGrid>, ad esempio. Se si visualizza una piccola griglia di valori di sola lettura o se si consente a un utente di modificare una tabella con milioni di record, il <xref:System.Windows.Forms.DataGridView> controllo fornirà una soluzione facilmente programmabile e efficiente per la memoria.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Riepilogo della tecnologia del controllo DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Riepiloga i concetti di controlloel'utilizzodiclassicorrelate.<xref:System.Windows.Forms.DataGridView>  
  
 [Architettura del controllo DataGridView](datagridview-control-architecture-windows-forms.md)  
 Descrive l'architettura del <xref:System.Windows.Forms.DataGridView> controllo, spiegando la gerarchia dei tipi e la struttura di ereditarietà.  
  
 [Scenari del controllo DataGridView](datagridview-control-scenarios-windows-forms.md)  
 Vengono descritti gli scenari più comuni in <xref:System.Windows.Forms.DataGridView> cui vengono utilizzati i controlli.  
  
 [Directory del codice del controllo DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Vengono forniti collegamenti a esempi di codice nella documentazione per <xref:System.Windows.Forms.DataGridView> varie attività. Questi esempi sono suddivisi in categorie in base al tipo di attività.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di colonne nel controllo DataGridView di Windows Form](column-types-in-the-windows-forms-datagridview-control.md)  
 Vengono illustrati i tipi di colonna <xref:System.Windows.Forms.DataGridView> nel controllo Windows Forms utilizzati per visualizzare le informazioni e consentire agli utenti di modificare o aggiungere informazioni.  
  
 [Visualizzazione di dati nel controllo DataGridView di Windows Form](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Fornisce argomenti che descrivono come popolare il controllo con i dati manualmente o da un'origine dati esterna.  
  
 [Personalizzazione del controllo DataGridView di Windows Form](customizing-the-windows-forms-datagridview-control.md)  
 Fornisce argomenti che descrivono come disegnare celle e righe personalizzate di <xref:System.Windows.Forms.DataGridView> e come creare tipi di cella, colonna e riga derivati.  
  
 [Ottimizzazione delle prestazioni nel controllo DataGridView di Windows Form](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Fornisce argomenti che descrivono come usare il controllo in modo efficiente per evitare problemi di prestazioni quando si lavora con grandi quantità di dati.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Controllo DataGridView](datagridview-control-windows-forms.md)
- [Funzionalità predefinite nel controllo DataGridView di Windows Form](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Gestione predefinita di tastiera e mouse nel controllo DataGridView di Windows Form](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
