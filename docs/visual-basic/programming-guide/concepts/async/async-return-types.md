---
title: Tipi restituiti asincroni
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 96d3a945a49a12f7c2d5d60e8ee59ce047a0bae6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347972"
---
# <a name="async-return-types-visual-basic"></a>Async Return Types (Visual Basic)

I metodi asincroni hanno tre possibili tipi restituiti: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> e void. In Visual Basic il tipo restituito void è scritto come routine [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md). For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Ogni tipo restituito viene esaminato in una delle sezioni seguenti e alla fine dell'argomento è disponibile un esempio completo che usa tutti i tre tipi.

> [!NOTE]
> Per eseguire l'esempio, è necessario avere installato Visual Studio 2012 o versioni successive e .NET Framework 4.5 o versioni successive nel computer.

## <a name="BKMK_TaskTReturnType"></a> Tipo restituito task(T)

The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.

Nell'esempio seguente il metodo asincrono `TaskOfT_MethodAsync` contiene un'istruzione return che restituisce un valore intero. La dichiarazione del metodo deve quindi specificare un tipo restituito di `Task(Of Integer)`.

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

Quando `TaskOfT_MethodAsync` viene chiamato da un'espressione await, l'espressione recupera il valore intero (valore di `leisureHours`) archiviato nell'attività restituita da `TaskOfT_MethodAsync`. For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).

Il codice seguente chiama e attende il metodo `TaskOfT_MethodAsync`. Il risultato viene assegnato alla variabile `result1`.

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

È possibile capire meglio il modo in cui ciò avviene separando la chiamata a `TaskOfT_MethodAsync` dall'applicazione di `Await`, come illustrato dal codice seguente. Una chiamata al metodo `TaskOfT_MethodAsync` che non viene immediatamente attesa restituisce un tipo `Task(Of Integer)`, come ci si aspetterebbe dalla dichiarazione del metodo. Nell'esempio, l'attività viene assegnata alla variabile `integerTask`. Poiché `integerTask` è un <xref:System.Threading.Tasks.Task%601>, contiene una proprietà <xref:System.Threading.Tasks.Task%601.Result> di tipo `TResult`. In questo caso, TResult rappresenta un tipo Integer. Quando si applica `Await` a `integerTask`, l'espressione await restituisce il contenuto della proprietà <xref:System.Threading.Tasks.Task%601.Result%2A> di `integerTask`. Il valore viene assegnato alla variabile `result2`.

> [!WARNING]
> La proprietà <xref:System.Threading.Tasks.Task%601.Result%2A> è una proprietà di blocco. Se si prova ad accedervi prima del completamento dell'attività, il thread attualmente attivo viene bloccato fino a quando l'attività non viene completata e il valore non è disponibile. Nella maggior parte dei casi, è consigliabile accedere al valore usando `Await` invece di accedere direttamente alla proprietà.

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

Le istruzioni di visualizzazione nel codice seguente verificano che i valori della variabile `result1`, della variabile `result2` e della proprietà `Result` siano identici. Si noti che la proprietà `Result` è una proprietà di blocco e non ci si deve accedere prima che la sua attività sia stata completata.

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="BKMK_TaskReturnType"></a> Tipo restituito Task

I metodi asincroni che non contengono un'istruzione return o che contengono un'istruzione return che non restituisce un operando hanno in genere il tipo restituito <xref:System.Threading.Tasks.Task>. Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously. Se si usa un tipo restituito `Task` per un metodo asincrono, un metodo chiamante può usare un operatore `Await` per sospendere il completamento del chiamante fino a quando il metodo asincrono chiamato non abbia terminato l'operazione.

Nell'esempio seguente il metodo asincrono `Task_MethodAsync` non contiene un'istruzione return. Di conseguenza, si specifica un tipo restituito `Task` per il metodo, che consente a `Task_MethodAsync` di essere atteso. La definizione del tipo `Task` non include una proprietà `Result` per archiviare un valore restituito.

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

`Task_MethodAsync` viene chiamato e atteso usando un'istruzione await invece di un'espressione await, simile all'istruzione chiamante per un metodo sincrono `Sub` o che restituisce void. The application of an `Await` operator in this case doesn't produce a value.

Il codice seguente chiama e attende il metodo `Task_MethodAsync`.

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows. Tuttavia, si noti che un tipo `Task` non ha una proprietà `Result` e che quando viene applicato un operatore await a un tipo `Task` non viene prodotto alcun valore.

Il codice seguente separa la chiamata di `Task_MethodAsync` dall'attesa dell'attività restituita da `Task_MethodAsync`.

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a> Tipo restituito void

The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages). Un tipo restituito void può essere usato anche per eseguire l'override di metodi che restituiscono void o per metodi che eseguono attività che possono essere categorizzate come "Fire and Forget". È consigliabile tuttavia restituire un tipo `Task` ogni volta che è possibile, perché un metodo asincrono che restituisce void non può essere atteso. Qualsiasi chiamante di questo metodo deve poter continuare fino al completamento senza attendere il completamento del metodo asincrono chiamato e il chiamante deve essere indipendente da qualsiasi eccezione o valore generato dal metodo asincrono.

Il chiamante di un metodo asincrono che restituisce void non può intercettare le eccezioni generate dal metodo ed è probabile che queste eccezioni non gestite provochino un errore dell'applicazione. Se si verifica un'eccezione in un metodo asincrono che restituisce <xref:System.Threading.Tasks.Task> o <xref:System.Threading.Tasks.Task%601>, l'eccezione viene archiviata nell'attività restituita e rigenerata durante l'attesa dell'attività. Di conseguenza, verificare che qualsiasi metodo asincrono in grado di produrre un'eccezione abbia un tipo restituito <xref:System.Threading.Tasks.Task> o <xref:System.Threading.Tasks.Task%601> e che sia impostata l'attesa per le chiamate al metodo.

Per altre informazioni su come intercettare eccezioni nei metodi asincroni, vedere [Istruzione Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Il codice seguente definisce un gestore eventi asincroni.

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="BKMK_Example"></a> Esempio completo

Il progetto Windows Presentation Foundation (WPF) seguente contiene gli esempi di codice di questo argomento.

 Per eseguire il progetto, effettuare i passaggi seguenti:

1. Avviare Visual Studio.

2. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**. Dall'elenco dei tipi di progetto scegliere **Applicazione WPF**.

4. Immettere `AsyncReturnTypes` come nome del progetto e scegliere **OK**.

     Il nuovo progetto verrà visualizzato in **Esplora soluzioni**.

5. Nell'Editor di codice di Visual Studio scegliere la scheda **MainWindow.xaml** .

     Se la scheda non è visibile, aprire il menu di scelta rapida per MainWindow.xaml in **Esplora soluzioni** e quindi scegliere **Apri**.

6. Nella finestra **XAML** di MainWindow.xaml sostituire il codice con quello seguente.

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     Nella finestra di **progettazione**di MainWindow.xaml verrà visualizzata una finestra contenente una casella di testo e un pulsante.

7. In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.

8. Sostituire il codice in MainWindow.xaml.vb con quello riportato di seguito.

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. Premere il tasto F5 per eseguire il programma e quindi scegliere il pulsante **Start** .

     The following output should appear:

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a>Vedere anche

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Procedura dettagliata: Accesso al Web con Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Flusso di controllo in programmi asincroni (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Operatore Await](../../../../visual-basic/language-reference/operators/await-operator.md)
