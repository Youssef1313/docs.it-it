---
title: 'Procedura dettagliata: Ereditarietà da un controllo Windows Forms con Visual Basic'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 378d7b0c67791e6c48e9859e0546594df3ccc85e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931009"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Procedura dettagliata: Ereditarietà da un controllo Windows Forms con Visual Basic
Con Visual Basic, è possibile creare controlli personalizzati avanzati tramite l' *ereditarietà*. L'ereditarietà consente di creare nuovi controlli che non solo conservano tutte le funzionalità proprie dei controlli Windows Forms standard, ma includono anche funzionalità personalizzate. In questa procedura verrà creato un controllo ereditato semplice denominato `ValueButton`. Questo pulsante erediterà la funzionalità dal controllo Windows Forms <xref:System.Windows.Forms.Button> standard e esporrà una proprietà personalizzata denominata. `ButtonValue`

## <a name="creating-the-project"></a>Creazione del progetto
 Quando si crea un nuovo progetto è necessario specificarne il nome per impostare lo spazio dei nomi radice, il nome dell'assembly e il nome del progetto e assicurarsi che il componente predefinito sia inserito nello spazio dei nomi corretto.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Per creare la libreria di controlli ValueButtonLib e il controllo ValueButton

1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto**.

2. Selezionare il modello di progetto **libreria di controllo Windows Forms** dall'elenco di progetti Visual Basic e digitare `ValueButtonLib` nella casella **nome** .

     Per impostazione predefinita il nome del progetto, `ValueButtonLib`, verrà assegnato anche allo spazio dei nomi radice. Lo spazio dei nomi radice viene utilizzato per qualificare i nomi dei componenti dell'assembly. Se ad esempio due assembly forniscono componenti denominati `ValueButton`, sarà possibile specificare il componente `ValueButton` utilizzando `ValueButtonLib.ValueButton`. Per ulteriori informazioni, vedere [Spazi dei nomi in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).

3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **UserControl1** e scegliere **Rinomina** dal menu di scelta rapida. Modificare il nome file in `ValueButton.vb`. Scegliere il pulsante **Sì** quando richiesto per rinominare tutti i riferimenti all'elemento di codice "UserControl1".

4. In **Esplora soluzioni** fare clic sul pulsante **Mostra tutti i file**.

5. Aprire il nodo **ValueButton.vb** per visualizzare il file del codice generato nella finestra di progettazione **ValueButton.Designer.vb**. Aprire il file nell'**editor di codice**.

6. Individuare l' `Class` istruzione, `Partial Public Class ValueButton`e modificare il tipo da cui il controllo eredita da <xref:System.Windows.Forms.UserControl> a <xref:System.Windows.Forms.Button>. Ciò consente al controllo ereditato di ereditare tutte le funzionalità del <xref:System.Windows.Forms.Button> controllo.

7. Individuare il `InitializeComponent` metodo e rimuovere la riga che assegna la <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> proprietà. Questa proprietà non esiste nel <xref:System.Windows.Forms.Button> controllo.

8. Per salvare il progetto, scegliere **Salva tutto** dal menu **File**.

     Si noti che non sarà più disponibile alcuna finestra di progettazione. Poiché il <xref:System.Windows.Forms.Button> controllo esegue un disegno personalizzato, non è possibile modificarne l'aspetto nella finestra di progettazione. La relativa rappresentazione visiva sarà esattamente identica a quella della classe da cui eredita (ovvero), <xref:System.Windows.Forms.Button>a meno che non venga modificata nel codice.

> [!NOTE]
> È comunque possibile aggiungere nell'area di progettazione i componenti che non dispongono di elementi dell'interfaccia utente.

## <a name="adding-a-property-to-your-inherited-control"></a>Aggiunta di una proprietà al controllo ereditato
 Un possibile utilizzo dei controlli Windows Forms ereditati è la creazione di controlli aventi aspetto e funzionalità identici ai controlli standard Windows Forms, ma che espongono proprietà personalizzate. In questa sezione verrà illustrata la modalità di aggiunta della proprietà `ButtonValue` al controllo.

### <a name="to-add-the-value-property"></a>Per aggiungere la proprietà Value

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ValueButton.vb**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Individuare l'istruzione `Public Class ValueButton`. Sotto questa istruzione digitare il seguente codice:

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     Questo codice consente di impostare i metodi per la memorizzazione e il recupero della proprietà `ButtonValue`. L'istruzione `Get` consente di impostare il valore restituito sul valore memorizzato nella variabile privata `varValue`, mentre l'istruzione `Set` consente di impostare il valore della variabile privata mediante la parola chiave `Value`.

3. Per salvare il progetto, scegliere **Salva tutto** dal menu **File**.

## <a name="testing-your-control"></a>Test del controllo
 I controlli non sono progetti autonomi e devono pertanto essere inseriti in un contenitore. Per testare il controllo, è necessario creare un progetto di test in cui eseguirlo. È inoltre necessario rendere il controllo accessibile al progetto di test compilandolo. In questa sezione verrà illustrato come compilare un controllo ed eseguirne il test in un Windows Form.

### <a name="to-build-your-control"></a>Per compilare il controllo

1. Scegliere **Compila soluzione** dal menu **Compila**.

     La compilazione dovrebbe essere completata senza errori del compilatore o avvisi.

### <a name="to-create-a-test-project"></a>Per creare un progetto di test

1. Scegliere **Aggiungi** dal menu **File**, quindi fare clic su **Nuovo progetto**. Verrà visualizzata la finestra di dialogo **Aggiungi nuovo progetto**.

2. Selezionare il nodo progetti Visual Basic e fare clic su **Windows Forms applicazione**.

3. Nella casella **Nome** digitare `Test`.

4. In **Esplora soluzioni** fare clic sul pulsante **Mostra tutti i file**.

5. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Riferimenti** del progetto di test, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida per visualizzare la finestra di dialogo **Aggiungi riferimento**.

6. Fare clic sulla scheda **Progetti**.

7. Scegliere la scheda **Progetti**. Il progetto `ValueButtonLib` verrà elencato in **Nome progetto**. Fare doppio clic sul progetto per cui si desidera aggiungere il riferimento al progetto di test.

8. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Test** e scegliere **Compila**.

### <a name="to-add-your-control-to-the-form"></a>Per aggiungere il controllo al modulo

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Form1.vb**, quindi scegliere **Visualizza finestra di progettazione** dal menu di scelta rapida.

2. Nella **Casella degli strumenti** fare clic su **Componenti ValueButtonLib**. Fare doppio clic su **ValueButton**.

     Nel modulo verrà visualizzato un controllo **ValueButton**.

3. Fare clic con il pulsante destro del mouse su **ValueButton**, quindi scegliere **Proprietà** dal menu di scelta rapida.

4. Nella finestra **Proprietà** esaminare le proprietà del controllo. Tali proprietà sono identiche a quelle esposte da un pulsante standard, con la differenza che è disponibile anche la proprietà `ButtonValue`.

5. Impostare la proprietà `ButtonValue` su `5`.

6. Nella scheda **tutti Windows Forms** della **casella degli strumenti**fare doppio clic su **etichetta** per aggiungere un <xref:System.Windows.Forms.Label> controllo al form.

7. Posizionare l'etichetta al centro del modulo.

8. Doppio clic su `ValueButton1`.

     Nell'**editor di codice** verrà visualizzato l'evento `ValueButton1_Click`.

9. Digitare la seguente riga di codice.

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Test** quindi scegliere **Imposta** come progetto di avvio dal menu di scelta rapida.

11. Scegliere **Avvia debug** dal menu **Debug**.

     Viene visualizzato `Form1`.

12. Fare clic su `Valuebutton1`.

     Il numero "5" verrà visualizzato in `Label1`, a significare che la proprietà `ButtonValue` del controllo ereditato è stata passata a `Label1` mediante il metodo `ValueButton1_Click`. Il controllo `ValueButton` erediterà tutte le funzionalità del pulsante standard per Windows Forms, ma esporrà una proprietà personalizzata aggiuntiva.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creazione di un controllo composito con Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Procedura: Visualizza un controllo nella finestra di dialogo Scegli elementi della casella degli strumenti](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Sviluppo di controlli Windows Form personalizzati con .NET Framework](developing-custom-windows-forms-controls.md)
- [Nozioni fondamentali sull'ereditarietà (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
