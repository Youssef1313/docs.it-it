---
title: "Procedura: Aggiungere i controlli senza un'interfaccia utente a Windows Forms"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987091"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Procedura: Aggiungere i controlli senza un'interfaccia utente a Windows Forms

Un controllo o un componente non visivo fornisce funzionalità per l'applicazione. A differenza di altri controlli, i componenti non forniscono un'interfaccia utente per l'utente e pertanto non devono essere visualizzati nell'area di Progettazione Windows Form. Quando un componente viene aggiunto a un modulo, il Progettazione Windows Form Visualizza un vassoio ridimensionabile nella parte inferiore del form in cui vengono visualizzati tutti i componenti. Dopo che un controllo è stato aggiunto alla barra dei componenti, è possibile selezionare il componente e impostarne le proprietà come qualsiasi altro controllo del modulo.

## <a name="add-a-component-to-a-windows-form"></a>Aggiungere un componente a un Windows Form

1. Aprire il modulo in Visual Studio. Per informazioni dettagliate, vedere [Procedura: Visualizza Windows Forms nella finestra di](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))progettazione.

2. Nella **casella degli strumenti**fare clic su un componente e trascinarlo nel form.

     Il componente verrà visualizzato nella barra dei componenti.

Inoltre, i componenti possono essere aggiunti a un modulo in fase di esecuzione. Si tratta di uno scenario comune, soprattutto perché i componenti non hanno un'espressione visiva, a differenza dei controlli che hanno un'interfaccia utente. Nell'esempio seguente viene aggiunto un <xref:System.Windows.Forms.Timer> componente in fase di esecuzione. Si noti che Visual Studio contiene una serie di timer diversi. in questo caso, usare un componente <xref:System.Windows.Forms.Timer> Windows Forms. Per ulteriori informazioni sui diversi timer in Visual Studio, vedere [Introduzione ai timer basati su server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).

> [!CAUTION]
> I componenti presentano spesso proprietà specifiche del controllo che è necessario impostare affinché il componente funzioni in modo efficace. Nel caso del <xref:System.Windows.Forms.Timer> componente seguente, impostare la `Interval` proprietà. Assicurarsi che, quando si aggiungono componenti al progetto, si impostano le proprietà necessarie per quel componente.

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Aggiungere un componente a un Windows Form a livello di codice

1. Creare un'istanza della <xref:System.Windows.Forms.Timer> classe nel codice.

2. Impostare la `Interval` proprietà per determinare l'intervallo di tempo tra i cicli del timer.

3. Configurare qualsiasi altra proprietà necessaria per il componente.

     Nel codice seguente viene illustrata la creazione <xref:System.Windows.Forms.Timer> di un `Interval` oggetto con il relativo set di proprietà.

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > È possibile esporre il computer locale a un rischio di sicurezza attraverso la rete facendo riferimento a un UserControl dannoso. Questo potrebbe costituire un problema solo nel caso di un utente malintenzionato che crea un controllo personalizzato dannoso, seguito da un'operazione erroneamente aggiunta al progetto.

## <a name="see-also"></a>Vedere anche

- [Controlli Windows Form](index.md)
- [Procedura: Aggiungere controlli a Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Procedura: Aggiunta di controlli ActiveX a Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Inserimento di controlli in Windows Form](putting-controls-on-windows-forms.md)
- [Impostazione delle etichette di singoli controlli Windows Form e creazione dei relativi tasti di scelta rapida](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Controlli da usare in Windows Form](controls-to-use-on-windows-forms.md)
- [Controlli Windows Form per funzione](windows-forms-controls-by-function.md)
