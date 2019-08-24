---
title: 'Procedura: Passare a un URL con il controllo WebBrowser'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015820"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Procedura: Passare a un URL con il controllo WebBrowser
Nell'esempio di codice riportato di seguito viene illustrato <xref:System.Windows.Forms.WebBrowser> come spostare il controllo in un URL specifico.

 Per determinare quando il nuovo documento è completamente caricato, gestire l' <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> evento. Per una dimostrazione di questo evento, vedere [procedura: Stampare con un controllo](how-to-print-with-a-webbrowser-control.md)WebBrowser.

## <a name="example"></a>Esempio

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Compilazione del codice
 L'esempio presenta i requisiti seguenti:

- Un controllo <xref:System.Windows.Forms.WebBrowser> denominato `webBrowser1`.

- Riferimenti agli assembly `System` e `System.Windows.Forms`.

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [Controllo WebBrowser](webbrowser-control-windows-forms.md)
- [Procedura: Stampare con un controllo WebBrowser](how-to-print-with-a-webbrowser-control.md)
