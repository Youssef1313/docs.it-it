---
title: 'Procedura: Creare un Form Master-Details mediante due controlli DataGridView di Windows Form'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: 16f23fac53cee5f6c007df6046e73cb7d9e1fbca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589208"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Procedura: Creare un modulo Master-Details usando due controlli DataGridView di Windows Forms
Nell'esempio di codice riportato di seguito viene creato un form Master-Details usando due controlli <xref:System.Windows.Forms.DataGridView> associati a due componenti <xref:System.Windows.Forms.BindingSource>. L'origine dati è un <xref:System.Data.DataSet> contenente le tabelle `Customers` e `Orders` del database di esempio SQL Server Northwind insieme a un oggetto <xref:System.Data.DataRelation> che mette in relazione le due tabelle tramite la colonna `CustomerID`.  
  
 Un oggetto <xref:System.Windows.Forms.BindingSource> è associato alla tabella `Customers` padre nel DataSet. Questi dati vengono visualizzati nel controllo <xref:System.Windows.Forms.DataGridView> master. L'altro oggetto <xref:System.Windows.Forms.BindingSource> è associato al primo connettore dati. Poiché la proprietà <xref:System.Windows.Forms.BindingSource.DataMember%2A> del secondo oggetto <xref:System.Windows.Forms.BindingSource> è impostata sul nome di <xref:System.Data.DataRelation>, il controllo dettagli <xref:System.Windows.Forms.DataGridView> associato visualizza le righe della tabella `Orders` figlio corrispondenti alla riga corrente nel controllo <xref:System.Windows.Forms.DataGridView> master.  
  
 Per una spiegazione completa di questo esempio di codice, vedere [procedura dettagliata: Creazione di un Form Master-Details mediante due Windows Form controlli DataGridView](creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Esempio  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
 Riferimenti agli assembly System, System.Data, System.Windows.Forms e System.XML.  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'archiviazione delle informazioni riservate, ad esempio la password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Procedura dettagliata: Creazione di un Form Master-Details mediante due controlli DataGridView di Windows Form](creating-a-master-detail-form-using-two-datagridviews.md)
- [Visualizzazione di dati nel controllo DataGridView di Windows Form](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Protezione delle informazioni di connessione](../../data/adonet/protecting-connection-information.md)
