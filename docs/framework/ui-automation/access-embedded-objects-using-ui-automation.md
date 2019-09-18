---
title: Accedere agli oggetti incorporati utilizzando l'automazione interfaccia utente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 110407079b37bce13bb6037d5755d2ef16a40214
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043959"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Accedere agli oggetti incorporati utilizzando l'automazione interfaccia utente
> [!NOTE]
> Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate su, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vedere [API di automazione di Windows: Automazione](https://go.microsoft.com/fwlink/?LinkID=156746)interfaccia utente.  
  
 Questo argomento illustra come [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] possa essere usato per esporre oggetti incorporati nel contenuto di un controllo testo.  
  
> [!NOTE]
> Gli oggetti incorporati possono includere immagini, collegamenti ipertestuali, pulsanti, tabelle o controlli ActiveX.  
  
 Gli oggetti incorporati sono considerati figli del provider di testo di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Ciò consente di esporli con la stessa struttura ad albero di automazione interfaccia utente di tutti gli altri elementi dell' [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] . La funzionalità, a sua volta, viene esposta con i pattern di controllo richiesti in genere dal tipo di controllo degli oggetti incorporati (ad esempio, poiché i collegamenti ipertestuali sono basati sul testo, supporteranno <xref:System.Windows.Automation.TextPattern>).  
  
 ![Oggetti incorporati in un contenitore di testo.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Un documento di esempio con contenuto testuale ("sai?" ...) e due oggetti incorporati, ovvero un'immagine di una balena e un collegamento ipertestuale di testo, usati come destinazione per gli esempi di codice.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come recuperare una raccolta di oggetti incorporati da un provider di testo di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Per il documento di esempio fornito nell'introduzione, verranno restituiti due oggetti (un elemento immagine e un elemento testo).  
  
> [!NOTE]
> All'elemento immagine sarà associato un testo intrinseco che descrive l'immagine, in genere in <xref:System.Windows.Automation.AutomationElement.NameProperty> (ad esempio, "A blue whale."). Tuttavia, quando si ottiene un intervallo di testo che si estende sull'oggetto immagine, né l'immagine né questo testo descrittivo vengono restituiti nel flusso di testo.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come ottenere un intervallo di testo da un oggetto incorporato in un provider di testo di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . L'intervallo di testo recuperato è un intervallo vuoto dove l'endpoint iniziale segue "… ocean.(space)" e l'endpoint finale precede il carattere "." di chiusura che rappresenta il collegamento ipertestuale incorporato (come illustrato dall'immagine fornita nell'introduzione). Anche se è un intervallo vuoto, non è considerato un intervallo degenere perché ha un'estensione diversa da zero.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern> può recuperare on oggetto incorporato basato su testo, ad esempio un collegamento ipertestuale. Tuttavia, sarà necessario ottenere un oggetto <xref:System.Windows.Automation.TextPattern> secondario dall'oggetto incorporato per esporne la funzionalità completa.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di TextPattern di automazione interfaccia utente](ui-automation-textpattern-overview.md)
- [Panoramica dei pattern di controllo per l'automazione interfaccia utente](ui-automation-control-patterns-overview.md)
- [Pattern di controllo di automazione interfaccia utente per i client](ui-automation-control-patterns-for-clients.md)
- [Aggiungere contenuto a una casella di testo usando l'automazione interfaccia utente](add-content-to-a-text-box-using-ui-automation.md)
- [Trovare ed evidenziare il testo usando l'automazione interfaccia utente](find-and-highlight-text-using-ui-automation.md)
