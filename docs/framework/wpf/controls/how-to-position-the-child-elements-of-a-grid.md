---
title: 'Procedura: Posizionare gli elementi figlio di un elemento Grid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: c508f45c1ea3d0925503d6fe5600498a0558d5ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770802"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Procedura: Posizionare gli elementi figlio di un elemento Grid
In questo esempio viene illustrato come utilizzare il metodo get e i metodi definiti nel set <xref:System.Windows.Controls.Grid> per posizionare elementi figlio.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente definisce un elemento padre <xref:System.Windows.Controls.Grid> elemento (`grid1`) che include tre colonne e tre righe. Un elemento figlio <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) viene aggiunto al <xref:System.Windows.Controls.Grid> nella posizione della colonna da zero, posizione zero della riga. <xref:System.Windows.Controls.Button> elementi rappresentano i metodi che possono essere chiamati per riposizionare le <xref:System.Windows.Shapes.Rectangle> elemento all'interno di <xref:System.Windows.Controls.Grid>. Quando un utente sceglie un pulsante, viene attivato il metodo correlato.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 L'esempio di codice seguente gestisce i metodi che il pulsante <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dagli eventi. L'esempio scrive queste chiamate ai metodi <xref:System.Windows.Controls.TextBlock> gli elementi correlati Usa metodi get per restituire i nuovi valori di proprietà come stringhe.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Ecco il risultato finale.
 
 ![uno screenshot viene illustrata un'interfaccia utente WPF con due colonne, la parte destra è presente una 3x3 griglia e sinistra è disponibili pulsanti per spostare un rettangolo colorato tra le colonne e righe della griglia](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Controls.Grid>
- [Cenni preliminari sugli elementi Panel](panels-overview.md)
