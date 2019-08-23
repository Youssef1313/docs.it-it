---
title: 'Procedura: Impostare rientri, rientri sporgenti e paragrafi puntati con il controllo RichTextBox di Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 9d095e3561cd346e6dbd99d1be7468f6ad5725a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960451"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Procedura: Impostare rientri, rientri sporgenti e paragrafi puntati con il controllo RichTextBox di Windows Forms
Il controllo <xref:System.Windows.Forms.RichTextBox> Windows Forms dispone di numerose opzioni per la formattazione del testo visualizzato. È possibile formattare i paragrafi selezionati come elenchi puntati impostando <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> la proprietà. È anche possibile usare le <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>proprietà <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, e <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> per impostare il rientro dei paragrafi rispetto ai bordi sinistro e destro del controllo e il bordo sinistro di altre righe di testo.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Per formattare un paragrafo come elenco puntato  
  
1. Impostare la proprietà <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> su `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>Per impostare il rientro di un paragrafo  
  
1. Impostare la <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> proprietà su un intero che rappresenta la distanza in pixel tra il bordo sinistro del controllo e il bordo sinistro del testo.  
  
2. Impostare la <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> proprietà su un intero che rappresenta la distanza in pixel tra il bordo sinistro della prima riga di testo nel paragrafo e il bordo sinistro delle righe successive nello stesso paragrafo. Il valore della <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> proprietà si applica solo alle righe in un paragrafo di cui è stato eseguito il wrapped sotto la prima riga.  
  
3. Impostare la <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> proprietà su un intero che rappresenta la distanza in pixel tra il bordo destro del controllo e il bordo destro del testo.  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    > Tutte queste proprietà vengono applicate a qualsiasi paragrafo contenente il testo selezionato, oltre che al testo digitato dopo il punto di inserimento corrente. Ad esempio, quando un utente seleziona una parola all'interno di un paragrafo e ne regola il rientro, le nuove impostazioni verranno applicate all'intero paragrafo contenente tale parola, nonché agli eventuali paragrafi immessi successivamente dopo il paragrafo selezionato. Per informazioni sulla selezione di testo a livello di <xref:System.Windows.Forms.TextBoxBase.Select%2A>codice, vedere.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.RichTextBox>
- [Controllo RichTextBox](richtextbox-control-windows-forms.md)
- [Controlli da usare in Windows Form](controls-to-use-on-windows-forms.md)
