---
title: Espressioni lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: f3f963167e1b3633cc5fe6e1f435e374cd272cce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345980"
---
# <a name="lambda-expressions-visual-basic"></a>Espressioni lambda (Visual Basic)

Un' *espressione lambda* è una funzione o una subroutine senza nome che può essere usata ovunque sia valido un delegato. Le espressioni lambda possono essere funzioni o subroutine e possono essere a riga singola o a più righe. È possibile passare valori dall'ambito corrente a un'espressione lambda.

> [!NOTE]
> L'istruzione `RemoveHandler` è un'eccezione. Non è possibile passare un'espressione lambda in per il parametro delegate di `RemoveHandler`.

Le espressioni lambda vengono create usando la parola chiave `Function` o `Sub`, proprio come si crea una funzione o una subroutine standard. Tuttavia, le espressioni lambda sono incluse in un'istruzione.

L'esempio seguente è un'espressione lambda che incrementa il relativo argomento e restituisce il valore. Nell'esempio viene illustrata la sintassi delle espressioni lambda a riga singola e a più righe per una funzione.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

L'esempio seguente è un'espressione lambda che scrive un valore nella console. Nell'esempio viene illustrata la sintassi delle espressioni lambda a riga singola e a più righe per una subroutine.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Si noti che negli esempi precedenti le espressioni lambda sono assegnate a un nome di variabile. Ogni volta che si fa riferimento alla variabile, viene richiamata l'espressione lambda. È anche possibile dichiarare e richiamare un'espressione lambda allo stesso tempo, come illustrato nell'esempio seguente.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Un'espressione lambda può essere restituita come valore di una chiamata di funzione, come illustrato nell'esempio nella sezione del [contesto](#context) più avanti in questo argomento, oppure passata come argomento a un parametro che accetta un tipo di delegato, come illustrato nell'esempio seguente.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Sintassi delle espressioni lambda

La sintassi di un'espressione lambda è simile a quella di una funzione o subroutine standard. Le differenze sono le seguenti:

- Un'espressione lambda non ha un nome.

- Le espressioni lambda non possono avere modificatori, ad esempio `Overloads` o `Overrides`.

- Le funzioni lambda a riga singola non utilizzano una clausola `As` per definire il tipo restituito. Al contrario, il tipo viene dedotto dal valore a cui viene restituito il corpo dell'espressione lambda. Se, ad esempio, il corpo dell'espressione lambda è `cust.City = "London"`, il tipo restituito è `Boolean`.

- Nelle funzioni lambda a più righe è possibile specificare un tipo restituito utilizzando una clausola `As` oppure omettere la clausola `As` in modo che il tipo restituito venga dedotto. Quando la clausola `As` viene omessa per una funzione lambda a più righe, il tipo restituito viene dedotto come tipo dominante da tutte le istruzioni `Return` nella funzione lambda a più righe. Il *tipo dominante* è un tipo univoco a cui tutti gli altri tipi possono ampliarsi. Se non è possibile determinare questo tipo univoco, il tipo dominante è il tipo univoco a cui tutti gli altri tipi nella matrice possono essere limitati. Se nessuno di questi tipi univoci può essere determinato, il tipo dominante è `Object`. In questo caso, se `Option Strict` è impostato su `On`, si verifica un errore del compilatore.

     Se, ad esempio, le espressioni fornite all'istruzione `Return` contengono valori di tipo `Integer`, `Long`e `Double`, la matrice risultante è di tipo `Double`. Sia `Integer` che `Long` si ampliano per `Double` e solo `Double`. `Double` è pertanto il tipo dominante. Per altre informazioni, vedere [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Il corpo di una funzione a riga singola deve essere un'espressione che restituisce un valore, non un'istruzione. Non esiste alcuna istruzione `Return` per le funzioni a riga singola. Il valore restituito dalla funzione a riga singola è il valore dell'espressione nel corpo della funzione.

- Il corpo di una subroutine a riga singola deve essere un'istruzione a riga singola.

- Le funzioni e le subroutine a riga singola non includono un'istruzione `End Function` o `End Sub`.

- È possibile specificare il tipo di dati di un parametro di espressione lambda usando la parola chiave `As` oppure il tipo di dati del parametro può essere dedotto. È necessario dedurre tutti i parametri con i tipi di dati specificati.

- i parametri `Optional` e `Paramarray` non sono consentiti.

- I parametri generici non sono consentiti.

## <a name="async-lambdas"></a>Espressioni lambda asincrone

È possibile creare facilmente espressioni lambda e istruzioni che incorporano l'elaborazione asincrona utilizzando le parole chiave dell'operatore [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [await](../../../../visual-basic/language-reference/operators/await-operator.md) . Nell'esempio seguente di Windows Form è presente un gestore eventi che chiama e attende un metodo asincrono, `ExampleMethodAsync`.

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

È possibile aggiungere lo stesso gestore eventi utilizzando un'espressione lambda asincrona in un' [istruzione AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Per aggiungere il gestore, aggiungere un modificatore `Async` prima dell'elenco di parametri lambda, come illustrato di seguito.

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Per altre informazioni su come creare e usare i metodi asincroni, vedere [programmazione asincrona con Async e await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Context

Un'espressione lambda condivide il contesto con l'ambito in cui è definito. Dispone degli stessi diritti di accesso di qualsiasi codice scritto nell'ambito che lo contiene. Questo include l'accesso a variabili membro, funzioni e Subs, `Me`e parametri e variabili locali nell'ambito contenitore.

L'accesso a variabili e parametri locali nell'ambito contenitore può estendersi oltre la durata di tale ambito. Fino a quando un delegato che fa riferimento a un'espressione lambda non è disponibile per Garbage Collection, viene mantenuto l'accesso alle variabili nell'ambiente originale. Nell'esempio seguente, la variabile `target` è locale per `makeTheGame`, il metodo in cui è definita l'espressione lambda `playTheGame`. Si noti che l'espressione lambda restituita, assegnata a `takeAGuess` in `Main`, ha ancora accesso alla variabile locale `target`.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Nell'esempio seguente viene illustrata l'ampia gamma di diritti di accesso dell'espressione lambda nidificata. Quando l'espressione lambda restituita viene eseguita da `Main` come `aDel`, accede a questi elementi:

- Campo della classe in cui è definito: `aField`

- Proprietà della classe in cui è definita: `aProp`

- Parametro del metodo `functionWithNestedLambda`, in cui è definito: `level1`

- Variabile locale di `functionWithNestedLambda`: `localVar`

- Parametro dell'espressione lambda in cui è annidato: `level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Conversione in un tipo delegato

Un'espressione lambda può essere convertita in modo implicito in un tipo delegato compatibile. Per informazioni sui requisiti generali per la compatibilità, vedere [conversione di un delegato rilassato](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Nell'esempio di codice seguente, ad esempio, viene illustrata un'espressione lambda che converte in modo implicito in `Func(Of Integer, Boolean)` o una firma del delegato corrispondente.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Nell'esempio di codice seguente viene illustrata un'espressione lambda che converte in modo implicito in `Sub(Of Double, String, Double)` o una firma del delegato corrispondente.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Quando si assegnano espressioni lambda a delegati o vengono passati come argomenti a procedure, è possibile specificare i nomi dei parametri ma omettere i relativi tipi di dati, consentendo ai tipi di essere ricavati dal delegato.

## <a name="examples"></a>Esempi

- Nell'esempio seguente viene definita un'espressione lambda che restituisce `True` se all'argomento nullable è assegnato un valore e `False` se il relativo valore è `Nothing`.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Nell'esempio seguente viene definita un'espressione lambda che restituisce l'indice dell'ultimo elemento in una matrice.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Vedere anche

- [Routine](./index.md)
- [Introduzione a LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegati](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Istruzione Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Istruzione Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Tipi di valori nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Procedura: Passare una routine a un'altra routine in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Procedura: Creare un'espressione lambda](./how-to-create-a-lambda-expression.md)
- [Conversione di tipo relaxed del delegato](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
