---
title: Automazione interfaccia utente e ridimensionamento dello schermo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 4e101fffbd7e53cadce0b621d73ade2d1459ba00
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237450"
---
# <a name="ui-automation-and-screen-scaling"></a>Automazione interfaccia utente e ridimensionamento dello schermo
> [!NOTE]
>  Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate sulle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere [Windows Automation API: Automazione interfaccia utente](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] consente agli utenti di modificare l'impostazione [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] in modo da visualizzare la maggior parte degli elementi dell' [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] sullo schermo con dimensioni maggiori. Benché questa funzionalità fosse già disponibile da tempo in [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], nelle versioni precedenti era necessario che il ridimensionamento fosse implementato dalle applicazioni. In [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], con Gestione finestre desktop viene applicato il ridimensionamento predefinito per tutte le applicazioni che non gestiscono direttamente tale funzionalità. Per le applicazioni client di automazione interfaccia utente è necessario tenere conto di questa funzionalità.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Ridimensionamento in Windows Vista  
 L'impostazione predefinita di [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] è 96, ovvero 96 pixel che occupano la larghezza o l'altezza di un pollice astratto. La misura esatta di un pollice dipende dalle dimensioni e dalla risoluzione fisica del monitor. Ad esempio, su un monitor con una larghezza di 12 pollici e una risoluzione orizzontale di 1280 pixel, una riga orizzontale di 96 pixel si estende per circa 9/10 di un pollice.  
  
 La modifica dell'impostazione dei [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] non corrisponde alla modifica della risoluzione dello schermo. Con le proporzioni dei [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ,  il numero di pixel fisici sullo schermo rimane lo stesso. Il ridimensionamento viene tuttavia applicato alle dimensioni e alla posizione degli elementi dell' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . È possibile eseguire il ridimensionamento automaticamente con Gestione finestre desktop per il desktop e per le applicazioni che non richiedono tale funzionalità in modo esplicito.  
  
 In effetti, quando l'utente imposta il fattore di scala su 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], un pollice verticale o orizzontale sullo schermo aumenta del 25%. Tutte le dimensioni vengono ridimensionate di conseguenza. L'offset di una finestra dell'applicazione dai bordi superiore e sinistro dello schermo aumenta del 25%. Se il ridimensionamento dell'applicazione è abilitato e l'applicazione non usa valori [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], le dimensioni della finestra aumentano nella stessa proporzione, con gli offset e le dimensioni di tutti gli elementi dell' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] che contiene.  
  
> [!NOTE]
>  Per impostazione predefinita, il ridimensionamento di Gestione finestre desktop non viene eseguito per le applicazioni che non usano valori[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]quando si impostano i [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] su 120, ma solo quando i [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] sono impostati su un valore personalizzato pari o maggiore di 144. È tuttavia possibile ignorare questo comportamento predefinito.  
  
 Il ridimensionamento dello schermo crea nuove sfide per le applicazioni che dipendono dalle coordinate dello schermo. Lo schermo contiene ora due sistemi di coordinate: fisico e logico. Le coordinate fisiche di un punto sono l'offset effettivo in pixel dalla parte superiore sinistra dell'origine. Le coordinate logiche sono gli offset così come si presenterebbero se i pixel fossero ridimensionati.  
  
 Si supponga di progettare una finestra di dialogo con un pulsante in corrispondenza delle coordinate (100, 48). Quando la finestra di dialogo viene visualizzata con l'impostazione predefinita di 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], il pulsante si trova in corrispondenza delle coordinate fisiche (100, 48). Con l'impostazione di 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], il pulsante si trova in corrispondenza delle coordinate fisiche (125, 60). Ma le coordinate logiche sono le stesse indipendentemente [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] impostazione: (100, 48).  
  
 Le coordinate logiche sono importanti in quanto garantiscono il comportamento coerente del sistema operativo e delle applicazioni indipendentemente dall'impostazione dei [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] . Ad esempio, la proprietà <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> restituisce in genere le coordinate logiche. Se si sposta il cursore su un elemento in una finestra di dialogo, le stesse coordinate vengono restituite indipendentemente dall'impostazione dei [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] . Se si disegna un controllo in corrispondenza delle coordinate (100, 100), il controllo viene disegnato su queste coordinate logiche e occupa la stessa posizione relativa con qualsiasi impostazione dei [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] .  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Ridimensionamento nei client di automazione interfaccia utente  
 Il [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API non usa le coordinate logiche. I metodi e le proprietà seguenti restituiscono coordinate fisiche o le accettano come parametri.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Per impostazione predefinita, non sarà possibile ottenere risultati corretti da questi metodi e proprietà in un'applicazione client di automazione interfaccia utente in esecuzione in un ambiente non a 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] . Ad esempio, poiché la posizione del cursore è definita in coordinate logiche, il client non può semplicemente passare tali coordinate al metodo <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> per ottenere l'elemento sotto il cursore. Inoltre, l'applicazione non sarà in grado di posizionare correttamente le finestre al di fuori dell'area client.  
  
 La soluzione è costituita da due parti.  
  
1. Innanzitutto, occorre fare in modo che l'applicazione client usi valori [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]. A tale scopo, chiamare la funzione [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `SetProcessDPIAware` all'avvio. In codice gestito, la dichiarazione seguente rende disponibile questa funzione.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Questa funzione rende compatibile con dpi, vale a dire che tutte le finestre appartenenti al processo verranno ridimensionate l'intero processo. Nel [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), ad esempio, le quattro finestre che costituiscono il rettangolo di evidenziazione si trovano in corrispondenza delle coordinate fisiche ottenute da automazione interfaccia utente, non delle coordinate logiche. Se il codice di esempio non sono compatibili con dpi, l'evidenziazione verrebbe disegnata in corrispondenza delle coordinate logiche sul desktop, con la conseguenza di un posizionamento errato in un ambiente non a 96 dpi.  
  
2. Per ottenere coordinate del cursore, chiamare la funzione [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `GetPhysicalCursorPos`. Nell'esempio riportato di seguito viene illustrato come dichiarare e usare questa funzione.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Non usare la proprietà <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Il comportamento di questa proprietà al di fuori delle finestre client in un ambiente non ridimensionato non è definito.  
  
 Se nell'applicazione viene eseguita comunicazione tra processi diretta con applicazioni che non usano valori [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], può essere necessario convertire le coordinate logiche e fisiche usando le funzioni [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `PhysicalToLogicalPoint` e `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Vedere anche

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
