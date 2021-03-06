---
title: Cenni preliminari sul controllo Splitter (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 934efd707f2a52da5ba604139c8e4510aad4606b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964464"
---
# <a name="splitter-control-overview-windows-forms"></a>Cenni preliminari sul controllo Splitter (Windows Form)
> [!IMPORTANT]
> Sebbene <xref:System.Windows.Forms.SplitContainer> sostituisce e aggiunge funzionalità al controllo <xref:System.Windows.Forms.Splitter> delle versioni precedenti, viene <xref:System.Windows.Forms.Splitter> mantenuto sia per la compatibilità con le versioni precedenti che per un uso futuro, se lo si sceglie.  
  
 I <xref:System.Windows.Forms.Splitter> controlli Windows Forms vengono usati per ridimensionare i controlli ancorati in fase di esecuzione. Il <xref:System.Windows.Forms.Splitter> controllo viene spesso usato nei form con controlli con lunghezze diverse di dati da presentare, ad esempio Esplora risorse, i cui riquadri dati contengono informazioni di larghezze variabili in momenti diversi.  
  
## <a name="working-with-the-splitter-control"></a>Utilizzo del controllo Splitter  
 Quando l'utente punta il puntatore del mouse sul bordo non ancorato di un controllo che può essere ridimensionato da un controllo Splitter, il puntatore cambia l'aspetto per indicare che è possibile ridimensionare il controllo. Con il controllo Splitter, l'utente può ridimensionare il controllo ancorato che si trova immediatamente prima. Pertanto, per consentire all'utente di ridimensionare un controllo ancorato in fase di esecuzione, ancorare il controllo da ridimensionare a un bordo di un contenitore e quindi ancorare un controllo Splitter allo stesso lato del contenitore.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.SplitContainer>
- [Procedura: Ancoraggio di controlli in Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Controlli da usare in Windows Form](controls-to-use-on-windows-forms.md)
