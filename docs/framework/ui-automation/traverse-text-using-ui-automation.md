---
title: Scorrere il testo utilizzando automazione interfaccia utente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 71df7c8f9dde388ffc4445389e105a4ad686539f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441870"
---
# <a name="traverse-text-using-ui-automation"></a>Scorrere il testo utilizzando automazione interfaccia utente
> [!NOTE]
> Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate su [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere l'argomento sull' [API Automazione interfaccia utente di Windows](/windows/win32/winauto/entry-uiauto-win32).  
  
 In questo argomento viene illustrato come usare [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] per scorrere il contenuto testuale di un documento in base a incrementi definiti da <xref:System.Windows.Automation.Text.TextUnit> .  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come scorrere il contenuto di un provider di testo di automazione interfaccia utente. Il metodo <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> sposta gli endpoint <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> e <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> di una classe <xref:System.Windows.Automation.Text.TextPatternRange>. Questo intervallo di testo è in genere un intervallo degenere che rappresenta il punto di inserimento.  
  
> [!NOTE]
> Poiché solo gli oggetti incorporati basati su testo sono considerati parte del flusso di testo, gli oggetti incorporati, ad esempio le immagini, non interessano `Move` o il relativo valore restituito.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Qualsiasi metodo che usa <xref:System.Windows.Automation.Text.TextUnit> rinvia al successivo valore più grande di <xref:System.Windows.Automation.Text.TextUnit> supportato se il valore specificato di <xref:System.Windows.Automation.Text.TextUnit> non è supportato dal controllo.  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di TextPattern di automazione interfaccia utente](ui-automation-textpattern-overview.md)
- [Aggiungere contenuto a una casella di testo usando l'automazione interfaccia utente](add-content-to-a-text-box-using-ui-automation.md)
- [Trovare ed evidenziare il testo usando l'automazione interfaccia utente](find-and-highlight-text-using-ui-automation.md)
- [Panoramica dei pattern di controllo per l'automazione interfaccia utente](ui-automation-control-patterns-overview.md)
- [Pattern di controllo di automazione interfaccia utente per i client](ui-automation-control-patterns-for-clients.md)
