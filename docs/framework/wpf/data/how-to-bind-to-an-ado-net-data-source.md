---
title: "Procedura: Eseguire il binding a un'origine dati ADO.NET"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 96f846db3f705972a4749460bf2c410483258572
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238419"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Procedura: Eseguire il binding a un'origine dati ADO.NET

In questo esempio viene illustrato come associare un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> controllo a un ADO.NET `DataSet`.

## <a name="example"></a>Esempio

In questo esempio viene usato un oggetto `OleDbConnection` per la connessione all'origine dati che è un file `Access MDB` specificato nella stringa di connessione. Dopo aver stabilito la connessione viene creato l'oggetto `OleDbDataAdapter` . L'oggetto `OleDbDataAdapter` esegue un'istruzione select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] per recuperare il recordset dal database. I risultati del comando [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] sono memorizzati in un `DataTable` di `DataSet` chiamando il metodo `Fill` di `OleDbDataAdapter`. `DataTable` in questo esempio è denominato `BookTable`. Nell'esempio viene quindi impostato il <xref:System.Windows.FrameworkElement.DataContext%2A> proprietà del <xref:System.Windows.Controls.ListBox> per il `DataSet` oggetto.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

È quindi possibile associare il <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> proprietà del <xref:System.Windows.Controls.ListBox> al `BookTable` del `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` è il <xref:System.Windows.DataTemplate> che definisce come vengono visualizzati i dati:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` converte un oggetto `int` in un colore. Con l'uso di questo convertitore, il <xref:System.Windows.Controls.TextBlock.Background%2A> colori del terzo <xref:System.Windows.Controls.TextBlock> viene visualizzato in verde se il valore di `NumPages` è inferiore a 350 rossa in caso contrario. L'implementazione del convertitore non viene visualizzata qui.

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Data.BindingListCollectionView>
- [Panoramica sul data binding](data-binding-overview.md)
- [Procedure relative alle proprietà](data-binding-how-to-topics.md)
