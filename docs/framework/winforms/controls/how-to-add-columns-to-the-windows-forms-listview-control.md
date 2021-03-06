---
title: 'Procedura: Aggiungere colonne al controllo ListView di Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 5c87d43513f2125945145445c61f689cdd9d2aaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345742"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Procedura: Aggiungere colonne al controllo ListView di Windows Forms
Nella visualizzazione dettagli i <xref:System.Windows.Forms.ListView> controllo può visualizzare più colonne per ogni elemento dell'elenco. È possibile usare le colonne da visualizzare all'utente di diversi tipi di informazioni su ogni elemento dell'elenco. Ad esempio, un elenco di file è stato possibile visualizzare il nome del file, tipo di file, le dimensioni e data che dell'ultima modifica apportata al file. Per informazioni sulla compilazione delle colonne dopo averli creati, vedere [come: Visualizzare elementi secondari nelle colonne con il Windows Form controllo ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Per aggiungere colonne a livello di codice  
  
1. Impostare il controllo <xref:System.Windows.Forms.ListView.View%2A> proprietà <xref:System.Windows.Forms.View.Details>.  
  
2. Usare la <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metodo della visualizzazione elenco <xref:System.Windows.Forms.ListView.Columns%2A> proprietà.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.ListView>
- [Controllo ListView](listview-control-windows-forms.md)
- [Panoramica del controllo ListView](listview-control-overview-windows-forms.md)
